.. _successes:

Successes
=========

This section describes some of the successfully implemented features and
subsystems and catalogs the source code repositories and online documentation
published during the project. These followed the contractual requirements
described in DHS Contract HSHQDC-13-C-B0013.

This project has successfully implemented a prototype for a deployable
open source distributed system. As described in this section and
Section :ref:`outcomes`, other projects have contemporaneously pursued
the same goal of producing a generally usable system comprised of open
source components. The DIMS project includes features that these other
projects do not (e.g., the integrated ``bats`` tests, the breadth and
depth of documentation, the features to support managing multiple
simultaneous deployments with private configuration).

The outcome of this project is by no means a production-ready commercially
sellable system, but the open source products are competitive in many aspects
with other projects created by larger teams of software engineering
professionals at commercial software companies. Further refinement within an
entity staffed and focused on bringing a product or service to the market could
quickly get there, but what is public now is far ahead of many of the
sample code that one can find by searching the internet, and the list of
resources in Section :ref:`resources` and Section :ref:`softwareproducts`
far exceeds anything that could be identified by the DIMS team.

What follows are sections identifying some of the key high level
achievements.

.. _ansible_playbooks:

Ansible Playbooks
-----------------

The most significant achievement of this project was the production and
refinement of
a set of Ansible playbooks, roles, and task files, capable of instantiating a
small-scale distributed system comprised of Ubuntu 14, Ubuntu 16, Debian 8, and
Container Linux by CoreOS systems, implementing an ``etcd``, ``consul``, and
Docker Swarm cluster. These playbooks share many similarities with those of
some other publicly available projects that were developed contemporaneously
with the DIMS Project, including the OpenCredo and Summit Route
Iterative Defense Architecture projects mentioned in Section
:ref:`integratedopensource`, as well as the `Fedora Project's Ansible playbooks`_,
Intel Corporation's `Trusted Analytics Platform`_, and `DebOps`_.

.. note::

   The PI reached out to each of these groups listed (with the exception of
   the Debops group) and two other projects using Ansible for multi-system
   deployment, to see if there was any possibility to collaborate or take
   development of DIMS Ansible playbooks.  The majority of these inquiries
   resulted in no response at all (despite multiple attempts in some cases.)
   One outreach resulted in a conversation that was a dead end, and another
   response suggested the chances of potential funding were low. Only one
   person engaged in multiple follow-on conversations, but no funding
   opportunities to support a collaboration could be identified.

   Two other projects were identified in the final days of the DIMS Project
   while investigating options for using `hashicorp/terraform`_ and
   `Digital Ocean`_; Cisco's `Mantl`_ and `DC/OS`_. These projects appear to
   have significantly larger and more well-resourced development teams. The
   fact that so many similar projects exist does confirm the viability of the
   direction taken in the DIMS Project.

..

.. _hashicorp/terraform: https://github.com/hashicorp/terraform
.. _Digital Ocean: https://www.digitalocean.com/
.. _Fedora Project's Ansible playbooks: https://infrastructure.fedoraproject.org/cgit/ansible.git
.. _Trusted Analytics Platform: https://01.org/tap
.. _trustedanalytics: https://github.com/trustedanalytics
.. _DebOps: https://github.com/debops
.. _Mantl: http://mantl.io/
.. _DC/OS: https://dcos.io/

The Ansible playbooks created by the DIMS project differ from each of
these in that they are designed to be multi-OS from the start, focused on
producing a stand-alone small-scale distributed system designed for security
incident response, with customization and configuration separated from the
playbooks repository to facilitate continued development and integration
of new tools capable of being managed independently of the public
``ansible-dims-playbooks`` repository.

These playbooks include the following features:

+ Support for Ubuntu 14.04, Ubuntu 16.04, Debian 8, Container Linux
  by CoreOS, and partial support for Mac OS X (Darwin) and RedHat
  Enterprise Linux.

+ Installation and pre-configuration of `Trident`_ trust group
  management portal.

+ Integrated multi-level testing using ``bats``.

+ Support for official SSL certificates using `Letsencrypt`_ and
  self-signed SSL certificates using https://github.com/uw-dims/ansible-role-ca

+ Support for automated backup and restoration of Trident PostgreSQL
  database and Letsencrypt certificates.

+ Support for version pinning of core subsystems across development
  and production hosts for improved distributed system stability.

+ Support for automated system-wide checks for availability of
  package updates, application of updates, and detection of
  required reboot, with option for email notification.

+ Support for isolated Vagrant Virtualbox virtual machines (including
  local copies of Ansible playbooks for testing branches and
  improved distributed system stability). This includes automated
  VM suspension upon host shutdown using, and multi-VM resumption
  after, using the ``dims.shutdown`` script.

.. _Letsencrypt: https://letsencrypt.org/
.. _Trident: https://trident.li

.. _tridentportal:

Trident Portal
--------------

The project began using the original Perl-based *ops-trust* portal system using
a hosted portal that was pre-configured. An initial Ansible playbook to deploy
a local instance was produced, but the team continued to use the hosted server.
In the final year of the project, Ansible playbook support for the new
Trident portal (re-written in Go, with both a command line and web application
graphical interface) was finally added and the ability to replicate the Trident
portal was achieved. Features to support customization of the portal's graphical
elements (banner image, default icon image for users who have not loaded their
own photo, logo image, and CSS style sheet settings for font and web page
colors) were added to support custom branding. These playbooks were used to
deploy a pilot instance to complete one of the final deliverables of the
project.

As mentioned in the previous section, along with the playbook for installing
Trident the ability to backup and restore both the Trident database and the
Letsencrypt SSL/TLS certificates was added. This allows easier development,
testing, and training with the Trident portal by simplifying deployment of two
portal servers at once (one for dev/test/training and the other for
"production" use.) Combined with the re-written Jenkins build scripts, an
improved mechanism for debugging and development of new Trident features is now
possible. (Testing of these features with volunteers associated with the
Trident portal in use by the ops-trust community is being discussed and will
move forward after the project end date.)


.. _continuousintegration:

Continuous Integration/Continuous Deployment
--------------------------------------------

Very early on, the project team established a set of Git source repositories
that were focused on discrete component services or functionality. Splitting
things up into discrete and focused repositories was done to establish a model
of modularity (to help make it easier to add new open source tools over time)
and to allow independent open source release of repositories.  In all, over 40
discrete repositories were created (some now deprecated, but the majority
providing functioning components addressing all of the requirements listed in
the contract and detailed in the :ref:`dimssr:dimssystemrequirements` document.

Next, a `Jenkins CI`_ server was set up and tied to the Git repositories using
Git post-commit hooks that trigger *build* jobs for source code and
documentation. Some build jobs then, in turn, trigger *deploy* jobs that push
the built products onto the systems that use them (see
:ref:`dimsdevguide:continuousintegration` for more detail on this process).

Throughout this entire workflow, log entries are generated (using a program
``logmon``) that publishes them on an AMQP channel where they can be monitored
from the DIMS Dashboard, monitored from a terminal session using the same
``logmon`` program, or collected from the logging channel for indexed storage.

.. _Jenkins CI: http://jenkins-ci.org/

.. _installBuildAutomation:

Install and Build Automation
----------------------------

System administrators are familiar with the steps of setting up a computer
systems, be it a server or a desktop development workstation, by starting with
an operating system installation ISO image, creating a bootable CD-ROM or USB
drive, creating accounts for the system administrator and some users, selecting
additional packages to install, and finally installing third-party open source
tools as needed.

This is a relatively simple process, and works well if the number of servers
and workstations is small, if the number of project members is small (and
turnover in staff is low and the team does not grow), if the software being
developed is limited in size and scope, and if things don't change very
quickly. Developers can even set up their own workstations and manage them.

.. _testintegration:

Integrated Tests
----------------

One of the requirements of the project was testing and validation
of the system components. A great deal of effort was spent in writing
comprehensive test plans and in performing two system-wide tests.
After the experience of doing these test plans and tests, a decision
was made to integrate the simplest set of tests as possible into
the normal operation of the system. The `Bats: Bash Automated Testing System`_
was chosen for its simplicity. A structured mechanism for embedding
tests into Ansible Playbook roles was developed, along with a script
to facilitate running tests named (not surprisingly) ``test.runner``.
This testing methodology is described in Section
:ref:`ansibledimsplaybooks:tests` of
:ref:`ansibledimsplaybooks:ansibledimsplaybooks`.

.. code-block:: none
   :caption: Successful test run from command line

    $ test.runner --level system --match pycharm
    [+] Running test system/pycharm
     ✓ [S][EV] Pycharm is not an installed apt package.
     ✓ [S][EV] Pycharm Community edition is installed in /opt
     ✓ [S][EV] "pycharm" is /opt/dims/bin/pycharm
     ✓ [S][EV] /opt/dims/bin/pycharm is a symbolic link to installed pycharm
     ✓ [S][EV] Pycharm Community installed version number is 2016.2.3

    5 tests, 0 failures

..

.. code-block:: none
   :caption: Failed unit test in Ansible playbook

    $ run.playbook --tags python-virtualenv
    . . .
    TASK [python-virtualenv : Run unit test for Python virtualenv] ****************
    Tuesday 01 August 2017  19:02:16 -0700 (0:02:06.294)       0:03:19.605 ********
    fatal: [dimsdemo1.devops.develop]: FAILED! => {
        "changed": true,
        "cmd": [
            "/opt/dims/bin/test.runner",
            "--tap",
            "--level",
            "unit",
            "--match",
            "python-virtualenv"
        ],
        "delta": "0:00:00.562965",
        "end": "2017-08-01 19:02:18.579603",
        "failed": true,
        "rc": 1,
        "start": "2017-08-01 19:02:18.016638"
    }

    STDOUT:

    # [+] Running test unit/python-virtualenv
    1..17
    ok 1 [S][EV] Directory /opt/dims/envs/dimsenv exists
    ok 2 [U][EV] Directory /opt/dims/envs/dimsenv is not empty
    ok 3 [U][EV] Directories /opt/dims/envs/dimsenv/{bin,lib,share} exist
    ok 4 [U][EV] Program /opt/dims/envs/dimsenv/bin/python exists
    ok 5 [U][EV] Program /opt/dims/envs/dimsenv/bin/pip exists
    ok 6 [U][EV] Program /opt/dims/envs/dimsenv/bin/easy_install exists
    ok 7 [U][EV] Program /opt/dims/envs/dimsenv/bin/wheel exists
    ok 8 [U][EV] Program /opt/dims/envs/dimsenv/bin/python-config exists
    ok 9 [U][EV] Program /opt/dims/bin/virtualenvwrapper.sh exists
    ok 10 [U][EV] Program /opt/dims/envs/dimsenv/bin/activate exists
    ok 11 [U][EV] Program /opt/dims/envs/dimsenv/bin/logmon exists
    not ok 12 [U][EV] Program /opt/dims/envs/dimsenv/bin/blueprint exists
    # (in test file unit/python-virtualenv.bats, line 54)
    #   `[[ -x /opt/dims/envs/dimsenv/bin/blueprint ]]' failed
    not ok 13 [U][EV] Program /opt/dims/envs/dimsenv/bin/dimscli exists
    # (in test file unit/python-virtualenv.bats, line 58)
    #   `[[ -x /opt/dims/envs/dimsenv/bin/dimscli ]]' failed
    not ok 14 [U][EV] Program /opt/dims/envs/dimsenv/bin/sphinx-autobuild exists
    # (in test file unit/python-virtualenv.bats, line 62)
    #   `[[ -x /opt/dims/envs/dimsenv/bin/sphinx-autobuild ]]' failed
    not ok 15 [U][EV] Program /opt/dims/envs/dimsenv/bin/ansible exists
    # (in test file unit/python-virtualenv.bats, line 66)
    #   `[[ -x /opt/dims/envs/dimsenv/bin/ansible ]]' failed
    not ok 16 [U][EV] /opt/dims/envs/dimsenv/bin/dimscli version is 0.26.0
    # (from function `assert' in file unit/helpers.bash, line 13,
    #  in test file unit/python-virtualenv.bats, line 71)
    #   `assert "dimscli 0.26.0" bash -c "/opt/dims/envs/dimsenv/bin/dimscli --version 2>&1"' failed with status 127
    not ok 17 [U][EV] /opt/dims/envs/dimsenv/bin/ansible version is 2.3.1.0
    # (from function `assert' in file unit/helpers.bash, line 18,
    #  in test file unit/python-virtualenv.bats, line 76)
    #   `assert "ansible 2.3.1.0" bash -c "/opt/dims/envs/dimsenv/bin/ansible --version 2>&1 | head -n1"' failed
    # expected: "ansible 2.3.1.0"
    # actual:   "bash: /opt/dims/envs/dimsenv/bin/ansible: No such file or directory"
    #

    PLAY RECAP ********************************************************************
    dimsdemo1.devops.develop   : ok=49   changed=7    unreachable=0    failed=1
    . . .

..

.. _python_virtualenv:

Python Virtualenv Encapsulation
-------------------------------

A frequently experienced point of friction within the team had to do with
differences in the tools being used by developers. One team member has ``git``
version ``2.1`` and the other has version ``1.8`` and can't access the repo the
night before a deadline. One person has the ``hub-flow`` tools and the other
does not, but they also don't know how to merge and push branches so their code
is not available to the team. Someone installs a broken version of an internal
tool and doesn't realize it when they try to test someone else's commits, so
their test fails when it should succeed and nobody knows why it is happening.

As a means of isolating and encapsulating a Python based shell environment to
facilitate development, testing, working on branches, and generally
experimenting in a non-destructive manner, the use of a standardized Python
virtual environment called ``dimsenv`` was implemented. This is a little
heavier-weight use of the Python ``virtualenv`` mechanism, encapsulating more
than just Python interpreter and ``pip`` installed packages.

The ``python-virtualenv`` role builds a specific version of Python, installs a
specific set of pinned ``pip`` packages, and also adds a series of programs to
the ``bin/`` directory so as to ensure the full set of commands that have been
documented in the :ref:`dimsdevguide:dimsdevguide` are available and at the
same revision level.

This not only saves time in setting up a development environment, but makes it
more consistent across systems and between development team members. Things
like testing new versions of Ansible is trivial.  You just clone the
``dimsenv`` environment (which has all the development tools in it already),
use ``workon`` to enable the new virtual environment, and ``pip install
ansible==$DESIRED_VERSION``. Then run the playbooks you want to test. It is
easy to switch back and forth, allowing development and debugging of playbooks
to be able to migrate to the latest version of Ansible more easily, while still
being able to fall back to the standard to get back to a stable build
environment. While this is an unconventional use of Python ``virtualenv``, it
works pretty well and saves lots of time.

.. _dashboard:

DIMS Dashboard
--------------

A functional dashboard web application was developed using distributed system
features provided by several VM compute servers over AMQP, with single-signon
tied to Google authentication. This dashboard supported user stories defined in
the :ref:`dimssr:dimssr` with built-in test capabilities. This was the most
production-ready and well-engineered components of the system.

.. _dashboard_1:

.. figure:: images/dashboard.png
   :alt: DIMS Dashboard
   :width: 70%
   :align: center

   DIMS Dashboard

..

Unfortunately, the dashboard server was one of the systems that was
only partially under Ansible control, using the older style Ansible playbooks
that have not been fully brought up to current standards. This has been
on the to-do list, along with rebuilding all of the other central
components (e.g., the Jenkins build server that failed when accidentally
upgraded to a version with non-backward compatible features).

.. _stixingest:

Ingest of STIX Documents
------------------------

Java bindings for STIX were produced to facilitate ingest of STIX version
1.1 documents into the DIMS system. (The current release of STIX is now
version 2.0.)

.. _tupelo:

Tupelo and Related Host Forensic Tools
--------------------------------------

A Java client/server application for manipulation of host file system disk
images and related metadata named "Tupelo" was produced as part of an earlier
National Science Foundation grant funded project.  It was enhanced with
inclusion of libraries for access TSK tools and manipulating virtual machine
disk images, and integrated into the early DIMS development deployment.

.. _Bats\: Bash Automated Testing System: https://github.com/sstephenson/bats#bats-bash-automated-testing-system


.. _softwareproducts:

Software Products and Documentation
-----------------------------------

The following table provides links to public source code repositories and
documentation.

.. _productstable:

.. list-table:: Software Products and Documentation
   :widths: 50,50
   :header-rows: 1

   * - Source repository
     - Documenation

   * - https://github.com/uw-dims/ansible-dims-playbooks
     - https://ansible-dims-playbooks.readthedocs.io

   * - https://github.com/uw-dims/device-files
     - (No additional documentation)

   * - https://github.com/uw-dims/dims-ad
     - https://dims-ad.readthedocs.io

   * - https://github.com/uw-dims/dims-dashboard
     - https://dims-dashboard.readthedocs.io

   * - https://github.com/uw-dims/dims-devguide
     - https://dims-devguide.readthedocs.io

   * - https://github.com/uw-dims/dims-jds
     - https://dims-jds.readthedocs.io

   * - https://github.com/uw-dims/dims-ocd/
     - https://dims-ocd.readthedocs.io

   * - https://github.com/uw-dims/dims-sr/
     - https://dims-sr.readthedocs.io

   * - https://github.com/uw-dims/dims-swplan
     - https://dims-swplan.readthedocs.io

   * - https://github.com/uw-dims/dims-training-manual
     - https://dims-training-manual.readthedocs.io

   * - https://github.com/uw-dims/dims-tp/
     - https://dims-tp.readthedocs.io

   * - https://github.com/uw-dims/dims-user-manual
     - https://dims-user-manual.readthedocs.io

   * - https://github.com/uw-dims/fuse4j
     - (No additional documentation)

   * - https://github.com/uw-dims/java-native-loader
     - (No additional documentation)

   * - https://github.com/uw-dims/stix-java
     - (No additional documentation)

   * - https://github.com/uw-dims/trident-training-manual
     - https://trident-training-manual.readthedocs.io

   * - https://github.com/uw-dims/trident-user-manual
     - https://trident-user-manual.readthedocs.io

   * - https://github.com/uw-dims/tsk4j
     - (No additional documentation)

   * - https://github.com/uw-dims/tupelo
     - (No additional documentation)

   * - https://github.com/uw-dims/xsdwalker
     - (No additional documentation)

..

