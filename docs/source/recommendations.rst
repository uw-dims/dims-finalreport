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

.. _ansibleFTW:

Focus on Ansible
----------------

The primary focus of anyone wanting to build on the project's successes is to
ensure everyone masters Ansible. That can't be stressed enough, since any
system that is not under Ansible control is a risk to stability and very costly
to fix or replace should something happen to it. Any host that is fully under
Ansible control can be quickly rebuilt, quickly reconfigured, and much more
easily debugged and diagnosed.

Rather than use SSH to log into hosts, whenver possible use ``ansible`` ad-hoc
mode. The ability to invoke modules directly using ``ansible`` not only helps
learn how the module work, but it also allows very powerful manipulation of any
or all hosts in the inventory at once. This makes debugging, configuring,
cleaning up, or any other task you need to perform, much easier and more
uniformly.

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
configruation adjustment with less disruption than with manual system
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

Standardize on Operating System(s)
----------------------------------

As much as possible, standardize on a small and manageable number of base
operating systems and versions. Every major or minor version difference (e.g.,
12.04.4 vs. 14.04.4 for Ubuntu Linux) or distribution difference (e.g., `Fedora
vs.  RedHat Enterprise Linux vs. CentOS`_) can have implications for
compatability of installed components and subcomponents, be they package
contents, libraries, or supported programs and utilities.

Using a configuration management program like Ansible helps by
expressing installation steps using different Ansible modules or plays,
though it does require engineering discipline to deal with complexity (above
and beyond what a Bash script would entail, for example) and to ensure the
right plays work the right way on the right operating system. This could mean
maintaining a large set of group variables (one for each alternative operating
system), using variables in inclusion directives to select from those
alternatives, and/or using "Ansible facts" derived at run time with logic (e.g.,
``when: ansible_os_family == "Debian"`` as a qualifier in a playbook)

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
*entire* system of systems in a separate deployment to ensure that tests can be
peformed to validate that all software works identically using the alternate
hypervisor.

The ``vncserver`` role was created to make it easier to remotely manage
long-running virtual machines using a GUI hypervisor control program. Using
CLI tools is also necessary, however, to more easily script operations
so they can be parallelized using Ansible ad-hoc mode, or scheduled
with ``cron`` or other background service managers.

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
One of the easiest ways is to start with a generic file has very little
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
``Makefile`` model is harder to use and those who are not experts in how
``make`` works (and are skilled enough to debug it with ``remake`` or other
low-level process tracing tools) have a hard time.

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

From the start, build everything to support at least two versions (``N`` and
``N-1``). In the case of DIMS, some systems were originally installed with
Ubuntu 12.04 LTS, but during the initial year a new set of scripts were
written to support Ubuntu 14.04 LTS (and the Ubuntu 12.04 LTS scripts were
abandoned). Since many systems were not originally created under full
Ansible control, or with automated build mechanisms, it was difficult
to migrate away from Ubuntu 12.04 on some systems and packages on those
systems slowly drifted and things broke.

If the build environment uses hard-coded version numbers like ``14.04`` and the
SHA256 hash of the installation ISO image for Ubuntu in a single variable, it
may become difficult (if not impossible, under the constraints of available
resources) to migrate to a new version of the operating system. The opposite --
and perhaps worse problem -- is having older version of an operating system
(e.g., Ubuntu 12.04 LTS) that were manually created to serve some key required
services, while the remainder of the build environment only was written to
support Ubuntu 14.04 LTS. The result is friction in upgrading, or having to
live with bugs or broken features because they cannot be upgraded.

If all of the required attributes of an operating system release (e.g., version
major and minor number, CPU architecture type, ISO download URL, SHA256 hash of
ISO, etc.) were all turned into variables and used consistently throughout the
OS build and Ansible deployment and configuration process, alternating between
the two is a simple matter of swapping out the file that defines the values for
these variables. This is where dictionaries (also known as "maps") come in
handy, allowing a single key (e.g., "ubuntu-14.04.5") to serve as a single
index to obtain all of the constituent variables in a consistent way.  If the
Packer build process, the Kickstart install process, and the Ansible playbooks,
all use different ways of defining these attributes, it becomes very difficult
to upgrade. If they all use a common dictionary and templating to produce
equivalent results across multiple tool using a single identifier, things are a
lot easier.

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
that can supports deprecation of old code, transition and migration to new
versions, as well as clean deletion of obsolete code when the time comes. Using
this mechanism of uniformly handling version support is much more modular than
using conditional constructs within programs, or mixing old and new files in a
single directory without any clear way to delineate or separate these files.




.. _Fedora vs. RedHat Enterprise Linux vs. CentOS: https://danielmiessler.com/study/fedora_redhat_centos/
.. _client.py: https://github.com/openstack/python-openstackclient/blob/master/openstackclient/identity/client.py#L24
.. _openstack/python-openstackclient: https://github.com/openstack/python-openstackclient/tree/master/openstackclient/identity
