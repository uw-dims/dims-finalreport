.. _enhancements:

Needed Enhancements
===================

.. epigraph::

   "*Perfection is finally attained not when there is no longer anything to
   add, but when there is no longer anything to take away.*"

   Antoine de Saint Exupéry, Terre des Hommes (1939)

..

There are several areas in the DIMS development architecture that are
more complex than is desirable, where things are difficult to use and
bugs often get in the way.  As the quote above atests, it is a challenge
to make things simple, elegant, and robust. Given limited resources,
time deadlines, and pressures to get things working, some components
of the DIMS project have attained the success of a prototype and
are now in need of reimplementation as a cleaner, tighter, next
major version.  This section describes some of those components
and thoughts on what to do next.

.. _packerVagrantWorkflow:

Packer and Vagrant Workflow Process
-----------------------------------

When the DIMS project began, and the team first began to work with
multiple Linux distributions (to follow guidance of each open source
tool producer's specified supported platform requirements), the
decision was made to use Packer for creating virtual machine
images from distribution disk image files (colloqually known as
**ISOs**, short for ISO 9660 format read-only boot images.).

To facilitate applying generic configuration settings and package
choices to multiple Linux distribution boot images, some helper
``Makefile`` rules files were created, allowing the dependency chain
to be defined such that Unix ``make`` can then optimize the
production of products. You don't want to have to perform every
step in a lengthy process (that involves downloading over a
Gigabyte of package files) every time you want to create a new
Vagrant virtual machine.

This process pipeline eventually included a Jenkins server
that would trigger ``ansible-playbook`` execution to implement
a complete continous integration/continuous deployment
environment. This process looked like that depicted in Figure
:ref:`packer_diagram`.

.. _packer_diagram:

.. figure:: images/packer_diagram.png
   :alt: Packer/Vagrant Workflow
   :width: 70%
   :align: center

   Packer/Vagrant Workflow

..

The options at the time were to use something like Chef, Puppet, Heat, or
Terraform. The choice had been made to use Ansible for system configuration
automation, which the team did not see as being compatible with Chef and
Puppet, and programs like Heat and Terraform were designed for much more larger
and more complicated multi-region cloud service deployments. We wanted DIMS
deployments to fit in a single server rack using a small external network
footprint, since the PRISEM project on which DIMS was to be built was built
that way.

In the long term, a solution that falls within the gap between a single server
rack with custom ``Makefile`` and scripts and something as complex as Openstack
or AWS CloudFormation is desired. This could be Terraform with custom
provisioners (though this would require specific programming expertise to
implement properly.)

In September of 2015, well into the DIMS project, Hashicorp came out with
"otto" and "nomad". [#otto1]_ These looked promising, but were immature and looked costly
to implement. In August 2016, Hashicorp announced they were decommissioning and
abandoning "otto". [#otto2]_ There is still a need for a tool like this, but we
continued to use the tools we had developed despite their limitations.
Continued simplification of these tools and integration with Ansible
through use of the inventory and templating scripts, Packer ``.json``
files, and ``Vagrantfile`` configuration files would help smooth
things out.

.. _kisckstart:

Normalization of Kickstart
--------------------------

Debian has a mechanism known as Kickstart that allows pre-configuration
of steps needed to perform an unattended ("hands-off") installation of
the operating system at boot time. This mechanism is used in DIMS
as part of the Packer workflow, and as part of the customized USB
thumb drive installer. It can also be made to work by Virtualbox
(or other hypervisors, for that matter) directly.

+ The Packer workflow uses inline commands to perform some initial
  system setup steps necessary to then use Ansible for the remainder
  of the system configuration.

+ The Vagrant workflow for Ubuntu and Debian uses some inline
  commands in the ``Vagrantfile`` for pre-Ansible customization,
  and some external scripts.

+ The Virtualbox Box file preparation for CoreOS uses external
  external scripts to prepare CoreOS for Ansible, and other
  ``Vagrantfile`` inline commands for boot-time customization.

+ The automated USB installer workflow uses the Kickstart ``pressed.cfg``
  file for what preparatory steps Kickstart is capable of performing,
  and a secondary pre-boot customization script that is downloaded and
  executed at install time for other pre-Ansible customization.

+ Manual creation of virtual machine guests or baremetal systems using
  the default Ubuntu or Debian installer (without using Kickstart)
  requires manual steps be performed to prepare the system for
  Ansible control.

The problem is, each of these workflows was created by separate team members at
different times, much of this without coordination or integration. Multiple
attempts were made to task team members with identifying all of the above and
reducing or refactoring the steps into a coherent and consistent set of
commonly-used scripts resulted. This resulted in some degree of simplification
and integration, but there is much work remaining to be done here.

Rather than having multiple incompatible inline shell mechanisms (which are the
easiest to implement, but least compatible means of accomplishing the same
tasks), a cleaner way to handle this situation is to reduce the steps required
in ``preseed`` steps to the bare minimum necessary to enable external Ansible
control.  Then these simpler ``pressed`` steps can be included as necessary by
each tool during Kickstart or the install-time tasks can be performed in Bash
shell scripts that can be called by each tool. This makes all of the
install-time steps consistent, configurable using Ansible, and shared across
tools. The remaining steps can then be turned into Ansible playbooks that can
be applied post-boot, again in a completely consistent manner.

.. _configurationManagementDatabase:

Configuration Management Database
---------------------------------

At the start of the project, a combination of variables stored in files that
could be exported through the environment into scripts and ``Makefile`` rules
and Ansible vars files was used. These mechanisms were not integrated and it
was difficult to switch between different sets of variables to support multiple
simultaneous deployments.  The simplistic and limited INI style inventory, with
group and host variable files, was easy to learn, but proved difficult to
manage for multiple deployments and for this reason its use held the project
back for a long time.

Having multiple deployments was always a project objective, but how to achieve
it using free and open source tools was not obvious to the team.  It was clear
that a configuration management database was needed that supported a more
object-oriented "inheritence" style mechanism of defining variables that would
more easily accomodate managing multiple simultaneous deployments.

The need here is for a system that behaves something like the way Openstack
supports a CLI for getting and setting variables in concert with a "cloud"
configuration file to control high-level storage locations that allow a single
interface to operate across multiple configuration databases. Ideally, it would
serve as what is called a "single point of truth" about not only data center
equipment (e.g., hardware devices, rack slots, switch ports, VLANs), but also
configuration specifics that would drive Ansible playbooks for configuration
and templating of scripts that run on the systems.  A lot of research was done,
but nothing seemed to be a good fit.  Commercial tools like Ansible Tower may
solve this problem, but that was neither in the budget for the project, nor did
that fall within the objective of using only free open source tools. Other
solutions were similarly focused on enterprise-level deployments and were not
suitable for our use.

The tools that seem to exist are all focused on large-scale cloud deployments
for massively-scaled, multi-datacenter deployments using a federated model.
Trying to add them to the mix would be too costly and divert too much attention
from other critical elements of system integration.  What is needed by projects
like this is a mechanism for many small-scale, single-datacenter deployments
that are configured locally, but pull much of their code from the public
repositories on GitHub.

The solution that was settled upon in the DIMS project was a combination of
most variables being defaulted in roles and a separete "private" directory for
each deployment that would hold customization details in the form of a YAML
inventory tree and local customized files and templates that playbooks in the
public ``ansible-dims-playbooks`` repository use before looking for generic
equivalents in the public repository. This allowed the ability to operate
multiple deployments in parallel with the public repository with less hassle,
though this is still not the ideal solution.

.. [#otto1] https://www.hashicorp.com/blog/otto/
.. [#otto2] https://www.hashicorp.com/blog/decommissioning-otto/
