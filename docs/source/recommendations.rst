.. _recommendations:

Recommendations for Follow-on Projects
======================================

This section includes recommendations for consideration in planning follow-on
projects, whether they use the DIMS Project software products or not, intended
to help reduce friction in the software development process. Any group
wanting to form a regional information sharing collaboration building
on the DIMS software base, or a small open source development project
wanting to use the platform for secure software development,
will want to consider these suggestions.

During the time of this project, we encountered all of the typical
problems that a team would have in the lifecycle of designing,
deploying, and maintaining a small-scale (on the order of dozens of
server components) distributed system. In order to have isolated
development, test, and production systems, the difficulty factor
goes up. To perform multiple production deployments and update
code over time further increases the difficulty factor. Eventually,
the lack of automation becomes a limiting factor at best, or
leads to an extremely unstable, fragile, and insecure final product at worst.

The benefit to those who chose to follow our lead will be a faster and
smoother journey than we experienced during the DIMS project period of
performance. All of the hurdles, mistakes, struggles, and ultimately the many
successes and achievements in distributed system engineering were not easily
found in the open source community. The :ref:`dimssr:dimssystemrequirements`
documents security practices and features that we have attempted to
incorporate to the greatest extent possible, in a way that can be improved
over time in a modular manner.  The system automation and continuous
integration/continuous deployment features help in implementing and
maintaining a secure system. (Red team application penetration testing will
further improve the security of the system through feedback about weaknesses
and deficiencies that crept in during development and deployment.)

.. _ansibleFTW:

Focus on System Build Automation
--------------------------------

From the first days of the project, the PI constantly told the team to *not*
build things by hand, since that does not scale and cannot be replicated. We
didn't need one hand-built system, we needed multiple systems for development,
testing, production, and anyone wanting to use the DIMS system needed to be able to
quickly and easily stand up a system. This can only be accomplished using
stable and well-documented build automation.

Ansible was chosen early on as what looked like the most promising system build
automation tool, so in this sense saying "focus on system build automation"
means "focus on mastering Ansible." Anyone wanting to build on the project's
successes, and avoid some of its challenges, must ensure that *all team members*
involved in development or system administration master
using Ansible. That can't be stressed enough, since any system that is not
under Ansible control is at risk of instability and very costly effort to fix
or replace should something happen to it. Any host that is fully under Ansible
control can be quickly rebuilt, quickly reconfigured, and much more easily
debugged and diagnosed.

Rather than use SSH to log into hosts, whenever possible use ``ansible`` ad-hoc
mode. The ability to invoke modules directly using ``ansible`` not only helps
learn how the module works, but it also allows very powerful manipulation of any
or all hosts in the inventory at once. This makes debugging, configuring,
cleaning up, or any other task you need to perform, much easier and more
uniform. Avoiding logging into hosts and remotely using the command line shell
also helps focus on controlling the configuration and using the automation
rather than hand-crafting uncontrolled system changes.

Using ``ansible-playbook`` with custom playbooks for complex tasks, or by
invoking a master playbook that includes all other playbooks, facilitates
performing an action across any or all hosts to keep things better in sync.
It documents the steps in a way that they can immediately be performed,
rather than documenting in English prose with code blocks that need to be
cut/pasted and edited manually to apply them when needed. The friction
caused by manual configuration of hosts is one of the biggest impediments
to building a complex and scalable system.

Last, but not least, by putting **all** configuration files under Ansible
control from the start enables much easier change management and incremental
configuration adjustment with less disruption than with manual system
administration. It is far easier to search Git history to figure out
what changed, or search a few directory trees to locate where a particular
variable is set or configuration file was customized. The ``ansible_managed``
line in configuration files on the end systems tells you precisely which
file was used by Ansible to create the current file, allowing you to make
changes and commit them to the Git repository to maintain history and
maintain control. Editing a file on the end host and introducing an error,
or accidentally deleting the file, make recovery difficult, while
reliably re-applying a role is simple and easy.

.. _standardOS:

Standardize Operating Systems
-----------------------------

As much as possible, standardize on a small and manageable number of base
operating systems and versions, and strive to keep up with the most recent
release (and perhaps one previous release) to avoid supporting too many
disparate features and one-off workarounds. Every major or minor version
difference (e.g., 12.04.4 vs. 14.04.4 for Ubuntu Linux) or distribution
difference (e.g., `Fedora vs.  RedHat Enterprise Linux vs. CentOS`_) can have
implications for computability of sub-components, be
they programs, libraries, or add-ons and utilities.

While this recommendation sounds simple, it is not. This task is made difficult
by the choices of supported base operating system(s) made by each of the open
source security tools you want to integrate. Great care needs to be taken in
making the decisions of which operating systems to support, balanced with
available expertise in the team for dealing with required debugging and
configuration management tasks.

Using a configuration management program like Ansible helps by expressing
installation steps using different Ansible modules or plays, though it does
require engineering discipline to deal with complexity (above and beyond what a
Bash script would entail, for example) and to ensure the right plays work the
right way on the right operating system. This could mean maintaining a large
set of group variables (one for each alternative operating system), using
variables in inclusion directives to select from those alternatives, and/or
using "Ansible facts" derived at run time with logic (e.g., ``when:
ansible_os_family == "Debian"`` as a conditional in a playbook)
Developing Ansible playbooks in a modular way that can easily accommodate
generalized support for multiple operating systems (e.g., using a "plug-in"
style model) is a more sophisticated way of writing playbooks that requires a
greater level of expertise of those writing the playbooks.  Such
expertise, or institutional support for employee training to achieve it, are
not always available.

.. _standardVM:

Standardize on Virtual Machine Hypervisor
-----------------------------------------

Attempting to use different hypervisors on different operating systems vastly
increases the friction in moving virtual machine resources from host to host,
from network to network, and from manual to automated creation. While it is
often possible to export a VM image, convert it to another format, and import
that VM back into another hypervisor, these steps require additional planning,
time and effort, and data transfer and storage resources that add friction to
the development process.

Start with a preferred hypervisor to support and take the time to migrate
legacy virtual machines to that preferred hypervisor, rather than attempting to
support part of the system with one hypervisor and the rest with another. If it
becomes necessary to support additional hypervisors, require replication of the
*entire* system of systems in a separate deployment (i.e., fully independent,
not sharing any resources in a way that couples the heterogeneous systems) to
ensure that tests can be performed to validate that all software works
identically using the alternate hypervisor.

The ``vncserver`` role [#vncserver]_ was created to make it easier to remotely manage
long-running virtual machines using a GUI hypervisor control program. Using
CLI tools is also necessary, however, to more easily script operations
so they can be parallelized using Ansible ad-hoc mode, or scheduled
with ``cron`` or other background service managers.

.. [#vncserver] https://github.com/uw-dims/ansible-dims-playbooks/blob/master/roles/vncserver/tasks/main.yml

.. _staticDynamicConfigs:

Manage Static Config Files Differently than User-controlled Files
-----------------------------------------------------------------

Managing files in ``/etc`` is different than ``$USER/.gitconfig``.  Let users
customize things, and add (merge) group content rather than wholesale replacing
files based on templates. Blindly installing configuration files is not
idempotent, and causes regression problems for users when an Ansible playbook
or role wipes out changes a user has made and takes the configuration file back
to an initial state.

There are several ways to do this, some more complicated than others.
One of the easiest ways is to start with a generic file that has very little
need for customization and will run on all systems, which in turn uses
a *drop-in* inclusion mechanism to in turn support inclusion of two
types of files:

#. Adding operating-system specific additions that are selected by some
   variable, such as output of ``uname -s`` as a component of the file
   name, or:

#. Allowing users to control their own customizations by including a
   file with some string like ``local`` in its name.

#. Supporting the ability for users to place their account configuration
   files in a personal Git repository that can be cloned and pulled
   to development systems so as to make the configurations consistent
   across hosts.

.. _robustBuild:

Robust, Flexible, and Replicable Build Environment
--------------------------------------------------

Some of the DIMS tools were initially prototyped using the Unix ``make``
utility and ``Makefile`` rules files. The ``make`` utility is nice in that it
supports dependency chaining. Things don't need to be rebuilt if the
constituent files used to build them have not changed. This works great for
source code, since programs are all static files (e.g., ``.c`` and ``.h`` files
for C programs) that can easily have timestamps checked to see if they require
recompiling to create new libraries or executable files. It is a little more
difficult when a script is produced from a template, which is produced from a
complex set of inventory files, host variable files, group variable files, and
command line variable definitions as is supported by Ansible. In that case, the
``Makefile`` model is harder to use, especially for those who are not experts in how
``make`` works and may not have the skills required to efficiently debug
it with ``remake`` or other low-level process tracing tools.

Tools like Jenkins or Rundeck provide a similar kind of dependency chaining
mechanism which may be preferable to ``make``, provided that programmers
carefully use variables and templating to produce the build jobs such that they
can be deployed to development, testing, staging, and production environments
without having to manually change hard-coded paths, etc.  This level of
generality may be difficult to set up, but is necessary to be able to scale and
replicate the build environment. This may sound like a "nice to have" thing,
but when cloning the system for deployment requires manually copying
build artifacts out of the one-and-only development build server, manually
setting up a mechanism allowing virtual machines to access the files,
and manually keeping it up to date as things change, the "must have"
nature makes itself painfully obvious.

.. _multiVersionSupport:

Avoid Painting Yourself into a Corner with Versions
---------------------------------------------------

From the start, build everything to support at least two operating system
release versions (the current release and one release back, or ``N`` and
``N-1``) and try to move as quickly as possible to the current release to avoid
getting locked in to older systems. This process is made easier if everyone
writing scripts and configuration files follows a "no hard-coded values" rule
for things like version numbers, hashes of distribution media for integrity
checking, file names of ISO installation disk images, etc.

If all of the required attributes of an operating system release (e.g., version
major and minor number, CPU architecture type, ISO download URL, SHA256 hash of
ISO, etc.) were referenced with variables and those variables used consistently
throughout the OS build and Ansible deployment and configuration process,
alternating between the two is a simple matter of alternating between two
sets of variable definitions.  This is where dictionaries (also known as
"maps") come in handy, allowing a single key (e.g., "ubuntu-14.04.5") to serve
as an index to obtain all of the constituent variables in a consistent
way.  If the Packer build process, the Kickstart install process, and the
Ansible playbooks, all define these attributes in different ways, it
becomes very difficult to upgrade versions.

Since operating systems are incrementally improving over time, the build
environment **must** take this into consideration to keep you from getting
painted into a metaphorical corner and finding it difficult to get out (without
spending a lot of time that should otherwise be directed to more productive
tasks).  Requiring support for version ``N`` and ``N-1`` simultaneously not
only provides a mechanism for testing package and configuration updates across
versions, but means that it will be much simpler when version ``N+1`` is
released to upgrade, test and plan a system-wide migration to the new OS
release.

Similarly, source code and system configuration (e.g., Ansible playbooks)
should also support versioning. An example of how to do this is found
in the GitHub source repository for `openstack/python-openstackclient`_.
The source code for `client.py`_ (starting at line 24 in `client.py`_,
and highlighted in the following excerpted code block) shows how this is done
by defining the ``DEFAULT_API_VERSION`` (which can be changed via the
``--os_identity_api_version`` command line option), and mappings of the option strings to directory names found in the
directory of `openstack/python-openstackclient`_ and to module names.

.. _clientpy:

.. code-block:: python
   :emphasize-lines: 1,2,5-7,12-14
   :caption: Excerpt of ``client.py`` showing version support

    DEFAULT_API_VERSION = '3'
    API_VERSION_OPTION = 'os_identity_api_version'
    API_NAME = 'identity'
    API_VERSIONS = {
        '2.0': 'openstackclient.identity.client.IdentityClientv2',
        '2': 'openstackclient.identity.client.IdentityClientv2',
        '3': 'keystoneclient.v3.client.Client',
    }
    
    # Translate our API version to auth plugin version prefix
    AUTH_VERSIONS = {
        '2.0': 'v2',
        '2': 'v2',
        '3': 'v3',
    }

..

Of course this requires greater engineering discipline when programming, but
had this technique been known and used from the start of the project it would
have resulted in a much more organized and structured source directory tree
that can support deprecation of old code, transition and migration to new
versions, as well as clean deletion of obsolete code when the time comes. Using
this mechanism of uniformly handling version support is much more modular than
using conditional constructs within programs, or mixing old and new files in a
single directory without any clear way to delineate or separate these files.


Budget for System Maintenance
-----------------------------

To paraphrase a joke in the programming world: "You have a problem. You decide
to solve your problem using free and open source software tools and operating
systems.  Now you have two problems." Sure, its a joke, but that makes it no
less true.

Trying to compose a system using open source parts that are constantly changing
requires constantly dealing with testing upgrades, updating version numbers
in Ansible playbook files, applying patches, debugging regression problems,
debugging version inconsistencies between systems, and updating
documentation. The more software subsystems and packages that are used, the
greater the frequency of changes that must be dealt with. Assume that somewhere
between 25% to 50%
of the project working time will be spent dealing with these issues.

The automation provided by Ansible, and the integration of unit and system
tests (see :ref:`ansibledimsplaybooks:tests`) helps immensely with identifying
what may be misconfigured, broken, or missing. Be disciplined about adding
new tests. Regularly running tests saves time in the long run. Make sure
that all team members learn to use these tools, as well as spend time
learning debugging techniques (see :ref:`ansibledimsplaybooks:debugging`).

.. _testingrecommendations:

Testing
-------

To avoid the issues described in Section :ref:`testingchallenges`, follow-on
projects are strongly advised to use these same MIL-STD-498 documents
(leveraging the Sphinx version of the templates used by the DIMS Project,
listed in Section :ref:`softwareproducts`) and the simpler BATS mechanism to
write tests to produce machine-parsable output.

We found that when BATS tests were added to Ansible playbooks, and executed
using the ``test.runner`` script after provisioning Vagrant virtual machines,
it was very easy to identify bugs and problems in provisioning scripts.
Friction in the development process was significantly reduced as a result.
This same mechanism can be extended to support the system-wide test and
reporting process. (See Section :ref:`testingenhancements`).


.. _Fedora vs. RedHat Enterprise Linux vs. CentOS: https://danielmiessler.com/study/fedora_redhat_centos/
.. _client.py: https://github.com/openstack/python-openstackclient/blob/master/openstackclient/identity/client.py#L24
.. _openstack/python-openstackclient: https://github.com/openstack/python-openstackclient/tree/master/openstackclient/identity
