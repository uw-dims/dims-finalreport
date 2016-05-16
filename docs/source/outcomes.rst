.. _outcomes:

Project Outcomes
================


Value of the Project
--------------------

As described in :ref:`dimsocd:dimsoperationalconceptdescription`,
the DIMS project has two primary expected outcomes: (1) an example platform for
building a complex integrated open source system for computer security incident
response, and (2) to transition this platform into the public sector to
support operational needs of State, Local, Territorial, and Tribal (SLTT)
government entities. The latest modification to the contract includes a
pilot deployment for use by the United States Secret Service in addition to
the open source release of source code and documentation.

The value of this project results from the (tangible and intangible) products
developed over the course of the period of performance. The team created and
used a continuous integration/continuous delivery model for taking software
source code, system automation instructions, software configuration, and
documentation, to build a prototype for an open source software integration
project. The resulting product can be used by an internal security operations
group (or managed security service provider) to create an open source incident
response capability.

.. _expectedoutcomes:

Expected Outcomes
-----------------

The primary outcome of the DIMS project is the open source publication of
software tools, system configurations, and documentation, following
implementation of the components in a prototype deployment.  A pilot
deployment for the United States Secret Service to use for their Electronic
Crimes Task Force (ECTF) program is also an outcome of this project.

A not-for-profit entity known as the Public Infrastructure Security
Collaboration and Exchange System (PISCES-NW, for "North West") was recently
formed. The Board of Directors has submitted a proposal to DHS to extend a
regional SLTT security monitoring project (formerly known as "PRISEM").
One of the PISCES-NW project's core objectives is to integrate DHS S&T-funded
research products.  Under this proposal, the DIMS PI will be engaged for a
limited time in the initial phase as a sub-contractor, focused on assisting
with implementation of selected DIMS open source products as requested by
the PISCES-NW Board of Directors.


.. _impacts:

Impacts
-------

The impact of the effort expended in this project goes beyond implementing one
set of open source service components for a single group. This model can be
replicated widely and improved upon by others faced with the same set of
challenges in developing an affordable and scalable incident response
capability. Over the course of the project, we have learned of several other
efforts to address a similar set of goals and have reached out (as time
permitted) to find common ground and try to develop collaborative
relationships that will have broad impact over time.


.. _theproduct:

The Product
-----------

The open source code, system configuration, and documentation produced during
the life of this project are the primary product(s). They document lessons
learned, provide an instructional path to follow, provide a guide for how to
continue moving forward, and illuminate the foundation we have established.
Using those components and instructions, the foundation for creating an
operational capability supporting several fundamental incident response use
cases can be set up in less time and effort than previously required. If widely
used, many of the unfinished features and latent bugs in the published code
base can be addressed by a larger number of people than could be supported by
the DIMS contract.

Getting the open source products from this contract to be widely used will not
be simple, or easy. As Maughan et al [MBLT13]_ discuss, projects do not sell
themselves and many attempts may be necessary (some resulting in failure)
before success is achieved. Outreach activities, and collaboration attempts
during the project to date have shown that language, pictures, shared
experience, and a clear description of the problems and proposed solution are
important (yet simultaneously a challenge to achieve.) Still, the conversations
we have had with multiple organizations are promising and it is likely that
DIMS products will be used in a variety of settings.

.. _theproblem:

The Problem it Solves
---------------------

The fundamental problem that this project aims to solve is to bring
capabilities of multiple open source products into a functioning whole. We
take a modular "platform" approach that allows for integrating chosen
open source components into a coherent whole. This is achieved by assembling
all of the necessary components and instructions for building a distributed
system with software development and operations ("DevOps") features that
support a modern software development and system integration team.

Open source software makes up the foundation of the Internet as we know it
today. OpenSSH, OpenSSL, NTP, and GnuPG are examples of successful open source
software used in many products, both open source and commercial.
Vulnerabilities like Heartbleed (CVE-2014-0160) have served as a wake-up call
for the need to improve the development and maintenance processes of these open
source projects to create a more secure foundation. The Linux Foundation began
`The Core Infrastructure Initiative`_, with the stated goal to "speed the pace
of open-source innovation while dramatically reducing global threats to online
security." The Criteria for software development in the Best Practices Badge
program GitHub page are rich, focusing primarily on software production. Where
they touch on aspects of the development environment and systems
administration, they provide less detail. The sections `Security of the
development environment`_ and `Deployment and operations`_ are short, general,
and do not share the same depth of specificity and guidance. The links to the
`GitHub security policy`_ and `Heroku security policy`_ provide a longer list
of tasks, but neither of these references goes deep enough to guide an open
source software development team in setting up and administering their own
infrastructure.  These are policy documents that say *what to do*, but not *how
to do it*. There are detailed examples in the larger Criteria document, and
links to working code to be used in development, but not working configurations
or specific steps for setting up the development environment.

Dr. Paul Vixie recently published a blog post, `Magical Thinking in Internet
Security`_ in which he points out the problem of complexity in implementing
security solutions, especially ones designed to detect and respond to
computer intrusions (while not being the *source* of intrusions, due to
security weaknesses in these complex systems that are not addressed
by the limited resources often invested in implementing these systems.
He starts his conclusion with this statement: "Increased complexity without
corresponding increases in understanding would be a net loss to a buyer."
DIMS products are intended to help shift the equation put forward
by Vixie, by helping make a less complex, more transparent, and easier
to secure platform than may otherwise be produced by
leveraging open source security tools from scratch.

.. _Magical Thinking in Internet Security: https://www.farsightsecurity.com/Blog/20160428-vixie-magicalthinking/

The products of the DIMS project provide a working and documented model
platform (or DevOps infrastructure) that can facilitate the secure integration
of open source components that (in and of themselves) are often hard to
deploy, and often are so insecurely implemented that they are effectively wide
open to the internet. This not only solves some of the infrastructure problems
alluded to by the Linux Foundation, but also addressing Vixie's example of
supporting organizations wanting to use open source security tools in concert
to address their trusted information sharing and security operations needs.

.. _The Core Infrastructure Initiative: https://www.coreinfrastructure.org
.. _Security of the development environment: https://github.com/linuxfoundation/cii-best-practices-badge/blob/master/doc/security.md#security-of-the-development-environment
.. _Deployment and operations: https://github.com/linuxfoundation/cii-best-practices-badge/blob/master/doc/security.md#deployment-and-operations
.. _GitHub security policy: https://help.github.com/articles/github-security/
.. _Heroku security policy: https://www.heroku.com/policy/security

Benefits
--------

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

.. [MBLT13] Douglas Maughan, David Balenson, Ulf Lindqvist, and Zachary Tudor. Crossing the "Valley of Death": Transitioning Cybersecurity Research into Practice. IEEE Security & Privacy, 11(2):14–23, 2013.
