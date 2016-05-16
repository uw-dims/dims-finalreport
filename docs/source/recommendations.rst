.. _recommendations:

Recommendations for Follow-on Projects
======================================

This section includes recommendations for consideration in planning
follow-on projects, whether they use DIMS products or not, intended
to help reduce friction in the software development process.

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

.. _Fedora vs. RedHat Enterprise Linux vs. CentOS: https://danielmiessler.com/study/fedora_redhat_centos/

.. _standardVM:

Standardize on Virtual Machine Hypervisor
-----------------------------------------

Attempting to use different hypervisors on different operating systems
vastly increases the friction in moving virtual machine resources from
host to host, from network to network, and from manual to automated
creation. While it is often possible to export a VM image, convert
it to another format, and import that VM back into another hypervisor,
these steps require additional planning, time and effort, and
data transfer and storage resources that add friction to the
development process.

Start with a preferred hypervisor to support and take the time to
migrate legacy virtual machines to that preferred hypervisor,
rather than attempting to support part of the system with one
hypervisor and the rest with another. If it becomes necessary
to support additional hypervisors, require replication of the
*entire* system of systems in a separate deployment to ensure
that tests can be peformed to validate that all software works
identically using the alternate hypervisor.

.. _staticDynamicConfigs:

Manage static configs differently than user-control configs
-----------------------------------------------------------

Managing files in ``/etc`` is different than ``$USER/.gitconfig``.
Let users customize things, and add (merge) group content rather than wholesale
replacement based on templates. This is not idempotent, and causes regression
problems for users when an Ansible playbook or role wipes out changes a user
has made and takes the configuration file back to an initial state.


.. _robustBuild:

.. todo::

   Talk about use of ``Makefile`` for Packer/Vagrant and how a monolithic
   build application, 

..

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
SHA256 hash of the installation ISO image for Ubuntu, it may become difficult
(if not impossible, under the constraints of available resources) to migrate to
a new version of the operating system. The opposite -- and perhaps worse
problem -- is having older version of an operating system (e.g., Ubuntu 12.04
LTS) that were manually created to serve some key required services, while the
remainder of the build environment only was written to support Ubuntu 14.04
LTS. The result is friction in upgrading, or having to live with bugs or broken
features because they cannot be upgraded.

If all of the required attributes of an operating system release (e.g., version
major and minor number, CPU architecture type, ISO download URL, SHA256 hash of
ISO, etc.) were all turned into variables and used consistently throughout
the OS build and Ansible deployment and configuration process, alternating
between the two is a simple matter of swapping out the file that defines
the values for these variables. If the Packer build process, the Kickstart
install process, and the Ansible playbooks, all use different ways of
defining these attributes, it becomes very difficult to upgrade.

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

.. code-block:: python
   :emphasize-lines: 1,2,5-7,12-14
   :caption: Except of ``client.py`` showing version support

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

.. _client.py: https://github.com/openstack/python-openstackclient/blob/master/openstackclient/identity/client.py#L24
.. _openstack/python-openstackclient: https://github.com/openstack/python-openstackclient/tree/master/openstackclient/identity
