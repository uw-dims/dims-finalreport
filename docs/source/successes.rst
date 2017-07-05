.. _successes:

Successes
=========

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

.. _dashboard:

DIMS Dashboard
--------------

.. TODO(dittrich): complete this section
.. todo::

   Complete this section.

..

.. _stixingest:

Ingest of STIX Documents
------------------------

.. TODO(dittrich): complete this section
.. todo::

   Complete this section.

..

