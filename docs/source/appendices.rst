.. _appendices:

Appendices
==========

.. _stix_dev_libraries:

STIX Development Libraries
--------------------------

`Subject: Re: [cti-users] Re: Announcing python-stix2`_

.. _Subject\: Re\: [cti-users] Re\: Announcing python-stix2: http://markmail.org/message/c5ahr2ykpcxxhfar

.. code-block:: none

    Sender: <cti-users@lists.oasis-open.org>
    Delivered-To: mailing list cti-users@lists.oasis-open.org
    Received: from lists.oasis-open.org (oasis-open.org [66.179.20.138])
        by lists.oasis-open.org (Postfix) with ESMTP id B1A965818580;
        Wed, 15 Mar 2017 09:48:17 -0700 (PDT)
    Message-ID: <58C96F55.4030104@apl.washington.edu>
    Subject: Re: [cti-users] Re: Announcing python-stix2
    Date: Wed, 15 Mar 2017 09:44:05 -0700
    From: Stuart Maclean <stuart@apl.washington.edu>
    To: "Back, Greg" <gback@mitre.org>, Eyal Paz <eyalp@checkpoint.com>,
            "cti@lists.oasis-open.org" <cti@lists.oasis-open.org>,
            "cti-users@lists.oasis-open.org" <cti-users@lists.oasis-open.org>
    References: <AAD76FB4-D5FE-41FA-9BDD-1EE6BBE4062D@mitre.org>
            <2956157C13955D458A922DDE028FEE7E0209A8F61D@IL-EX10.ad.checkpoint.com>
            <D3938F78-9B27-48B2-87BA-E57803DEBA81@mitre.org>
    In-Reply-To: <D3938F78-9B27-48B2-87BA-E57803DEBA81@mitre.org>
    
    On 03/15/2017 09:22 AM, Back, Greg wrote:
    >
    > Hi Eyal,
    >
    > MITRE isn't working on anything, and I'm not personally aware of
    > anyone else who is either. But if someone is, hopefully they're on one
    > of these lists and will respond.
    >
    > Greg
    
    Greg, all,
    
    I have followed the STIX development over the past couple of years, and
    even developed a Java library for STIX manipulation, see
    https://github.com/uw-dims/stix-java. That was when STIX 1.1 was current.
    
    I watched with some dismay as the XML schema way of doing things in STIX
    1.1 was dismantled in favor of JSON for STIX 2.  While XML schemas are
    complicated, they are very precise, and a document can be checked
    against a schema to assert its validity.  Further, the richness of tools
    for XML schemas, notably the JAXB/xjc tools for Java, gives developers a
    huge leg-up in implementing an API for STIX manipulation.  I just
    cranked the JAXB handle over the .xsd file set, and hey presto I had a
    set of Java classes with which to start my API. 
    
    Going out on a limb here, I also think that Java developers LIKE more
    discipline that Python developers.  Static typing vs duck typing?  The
    XML schema way of representing information is disciplined, and leads to
    fewer 'You meant X? I thought you meant Y' gotchas at runtime.
    Extrapolating, I think the JSON way of data representation is less
    disciplined than the XML way, hence the natural inclination of Python
    developers to prefer JSON.
    
    Looking at the STIX 2 specs, I admire effort the authors must have put
    in.  But from a library builder's point of view, there being no
    machine-ingestable docs (ie the xsd files in STIX 1.1), I am back to
    square one (if I have missed any machine-readable docs, I apologize).
    
    So, in a nutshell, my own feeling is that there will be no Java-language
    STIX 2 manipulation tools, a sad fact, and I sincerely hope I am wrong
    in this respect.  I do know that I won't add to my STIX 1.1 Java effort.
    
    Stuart

    ----

..

.. _references:

Reference Links
---------------

.. note::

    Over the life of the project, the PI lead the effort to research new
    technologies and guide the project team in learning these technologies in
    order to leverage them to acheive the integration goals of the project. The
    best references were organized and maintained as part of the PI's home page
    and all team members where urged to look there first and to let the PI know
    when they find new information that is not already there. These references
    are included here to help guide anyone else following this same path.

..

.. _containerization:

Containerization, Virtualization, "Microservice Architectures"
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+ `Microservices`_, Wikipedia
+ `Microservices: a definition of this new architecture`_, my Martin Fowler
+ `Operating-system-level virtualization`_ (a.k.a., "containers"), Wikipedia
+ `Linux Containers`_
    + `Container Overview`_, from CoreOS
+ `When to use containers (and when not to)`_, by Steven Vaughan-Nichols, May 15, 2017
+ `The Twelve-Factor App`_ ("`The twelve-factor methodology can be applied to apps written in any programming language, and which use any combination of backing services (database, queue, memory cache, etc).`")

.. _Microservices: https://en.wikipedia.org/wiki/Microservices
.. _Microservices\: a definition of this new architecture: http://martinfowler.com/articles/microservices.html
.. _Operating-system-level virtualization: http://en.wikipedia.org/wiki/Operating-system-level_virtualization
.. _Linux Containers: https://linuxcontainers.org
.. _Container Overview: https://coreos.com/using-coreos/containers/
.. _When to use containers (and when not to): https://insights.hpe.com/articles/when-to-use-containers-and-when-not-to-1705.html
.. _The Twelve-Factor App: http://12factor.net


.. _docker:

Docker
^^^^^^

    .. caution::

        Docker and all the related entities in the Docker ecosystem are
        changing **constantly** (and at a fast pace) so many of the resources below can become
        outdated or obsolete in a matter of months. `Docker Releases`_ occur
        regularly, so pay attention to dates and version numbers in the
        resources below when considering implementing something, but also look
        for useful tips and tricks that may still be relevant over time. Also,
        you may want to `Subscribe to Docker Weekly Newsletter`_ to maintain
        your own situational awareness of updates and high-quality articles,
        blog posts, and videos that can help you keep up.

    ..

.. _Docker Releases: https://blog.docker.com/category/docker-releases/
.. _Subscribe to Docker Weekly Newsletter: http://www.docker.com/subscribe_newsletter/


Docker intro
""""""""""""

+ `Docker ("Build, ship, and run any application, anywhere.")`_
+ `Docker: Build, Ship and Run Any App, Anywhere`_, by Martijn Dwars, Wiebe van Geest, Rik Nijessen and Rick Wieman
+ `Docker Reference Architecture: Designing Scalable, Portable Docker Container Networks`_, by Mark Church, Docker web site, October 18, 2016
+ `Docker Command Line`_
+ `Jeff Lindsay on Best Practices for Working with Containers and Docker`_
+ GitHub `docker/docs/sources/articles/dockerfile_best-practices.md`_ (Best practices for writing Dockerfiles)
+ `Cooking with Docker: useful tips for beginners`_, by Blair Hudson
+ `Docker traps (and how to avoid them)`_, by Mr. Blue Coat
+ `What is Docker?`_
+ `Introduction to Docker`_, Solomon Hykes (dotCloud founder and CTO of Docker), Twitter University
+ `5 Reasons to Start Using Docker`_, by David Bolton, June 1, 2015
+ GitHub `prakhar1989/docker-curriculum`_ ("A comprehensive tutorial on getting started with Docker! http://prakhar.me/docker-curriculum/")
+ `Play with Docker classroom`_, Docker web site

.. _Docker ("Build, ship, and run any application, anywhere."): https://www.docker.com/
.. _Docker\: Build, Ship and Run Any App, Anywhere: http://delftswa.github.io/chapters/docker/index.html
.. _Docker Reference Architecture\: Designing Scalable, Portable Docker Container Networks: https://success.docker.com/Datacenter/Apply/Docker_Reference_Architecture%3A_Designing_Scalable%2C_Portable_Docker_Container_Networks
.. _Docker Command Line: https://docs.docker.com/reference/commandline/cli/
.. _Jeff Lindsay on Best Practices for Working with Containers and Docker: http://www.infoq.com/interviews/lindsay-docker
.. _docker/docs/sources/articles/dockerfile_best-practices.md: https://github.com/docker/docker/blob/master/docs/sources/articles/dockerfile_best-practices.md
.. _Cooking with Docker\: useful tips for beginners: http://blairhudson.com/post/114211974513/cooking-with-docker-useful-tips-for-beginners
.. _Docker traps (and how to avoid them): http://mrbluecoat.blogspot.com/2014/10/docker-traps-and-how-to-avoid-them.html
.. _What is Docker?: https://youtu.be/aLipr7tTuA4
.. _Introduction to Docker: https://youtu.be/Q5POuMHxW-0
.. _5 Reasons to Start Using Docker: http://insights.dice.com/2015/06/01/5-reasons-to-start-using-docker/
.. _prakhar1989/docker-curriculum: https://github.com/prakhar1989/docker-curriculum
.. _Play with Docker classroom: http://training.play-with-docker.com/


.. _tipsandtricks:

Tips and Tricks for More Advanced Docker Use
""""""""""""""""""""""""""""""""""""""""""""

+ `What’s eating my disk? Docker System Commands explained`_, by Nils De Moor, April 12, 2017
+ `Docker Container Anti Patterns`_, by Arun Gupta, October 30, 2016
+ `What's New In Docker 1.12`_, by Emmet O'Grady, August 2, 2016
+ `Docker Tips And Tricks: Some tips about running and building with docker`_, by Luís Armando Bianchin, February 15, 2016
+ `Flexible Docker entrypoint scripts`_, by `camptocamp SA`_, March 22, 2016
+ `Deploying public keys in Docker containers`_, by `camptocamp SA`_, March 22, 2016
+ `When and why should I use apt-get update?`_, stackexchange, May 19, 2014
+ `Best practices for writing Dockerfiles`_, Docker.com web site
+ `Create a base image`_, Docker.com web site
+ `Building good docker images`_, by Jonathan Berghnoff, October 3, 2014
+ `Where are my containers? Dockerized service discovery with Consul`_, by Jose Luis Ordiales, January 23, 2015
+ `Automatic container registration with Consul and Registrator`_, by Jose Luis Ordiales, February 3, 2015
+ `Trapping signals in Docker containers`_, by Grigoriy Chudnov, April 7, 2015
+ `Docker Inspect Template Magic`_, by Adrian Mouat
+ `Wrangling Grafana and InfluxDB into a Docker image`_, by Si Beaumont, February 17, 2016
+ `An Example of Docker Multi Host Clustering Part 1`_, by Joshua Davis, January 20, 2016
+ `An Example of Docker Multi-Host Networking with Hadoop - Part 2`_, by Joshua Davis, February 10, 2016
+ `An Example of Docker Multi-Host Networking With Hadoop Part 3 - Validating your Swarm Cluster`_, by Joshua Davis, February 18, 2016
+ See also: `dockercleanup`_


.. _What’s eating my disk? Docker System Commands explained: https://cntnr.io/whats-eating-my-disk-docker-system-commands-explained-d778178f96f1
.. _Docker Container Anti Patterns: http://blog.arungupta.me/docker-container-anti-patterns/
.. _What's New In Docker 1.12: http://blog.nimbleci.com/2016/08/03/whats-new-in-docker-1.12/
.. _Docker Tips And Tricks\: Some tips about running and building with docker: http://blog.labianchin.me/2016/02/15/docker-tips-and-tricks
.. _Flexible Docker entrypoint scripts: https://www.camptocamp.com/en/actualite/flexible-docker-entrypoints-scripts/
.. _Deploying public keys in Docker containers: https://www.camptocamp.com/en/actualite/deploying-public-keys-in-docker-containers/
.. _camptocamp SA: https://www.camptocamp.com/
.. _When and why should I use apt-get update?: http://unix.stackexchange.com/questions/131009/when-and-why-should-i-use-apt-get-update
.. _Best practices for writing Dockerfiles: https://docs.docker.com/articles/dockerfile_best-practices/
.. _Create a base image: https://docs.docker.com/engine/userguide/eng-image/baseimages/
.. _Building good docker images: http://jonathan.bergknoff.com/journal/building-good-docker-images
.. _Where are my containers? Dockerized service discovery with Consul: http://jlordiales.me/2015/01/23/docker-consul/
.. _Automatic container registration with Consul and Registrator: http://jlordiales.me/2015/02/03/registrator/
.. _Trapping signals in Docker containers: https://medium.com/@gchudnov/trapping-signals-in-docker-containers-7a57fdda7d86
.. _Docker Inspect Template Magic: http://container-solutions.com/2015/03/docker-inspect-template-magic/
.. _Wrangling Grafana and InfluxDB into a Docker image: http://simonjbeaumont.com/posts/docker-dashboard
.. _An Example of Docker Multi Host Clustering Part 1: http://javaarchramble.blogspot.com/2016/01/an-example-of-docker-multi-host.html
.. _An Example of Docker Multi-Host Networking with Hadoop - Part 2: http://javaarchramble.blogspot.com/2016/02/an-example-of-docker-multi-host.html
.. _An Example of Docker Multi-Host Networking With Hadoop Part 3 - Validating your Swarm Cluster: http://javaarchramble.blogspot.com/2016/02/an-example-of-docker-multi-host_18.html



.. _dockerbooks:

Books and guides (and a mindmap!)
"""""""""""""""""""""""""""""""""

    + The `Docker Ecosystem`_ (mindmap by Krishnan Subramanian)
    + `The Docker Book`_, by James Turnbull
        + `Sample Chapter`_
        + `Code examples`_

    + `O'Reilly Docker cookbook`_, by Sebastien Goasguen
        + GitHub `how2dock/docbook`_ (Sample code and Vagrant files for O'Reilly Docker cookbook)

    + `Welcome to the Docker User Guide`_
        + `Understanding Docker`_
        + `Network Configuration`_
        + `Docker Compose`_
            + See also: `How to use Docker Compose to run complex multi container apps on your Raspberry Pi`_ and the RaspberryPi section of :ref:`smallformfactor`.

    + `How to Use Docker on OS X: The Missing Guide`_, by Chris Jones


.. _Docker Ecosystem: https://www.mindmeister.com/389671722/docker-ecosystem
.. _The Docker Book: http://www.dockerbook.com/
.. _Sample chapter: http://www.dockerbook.com/TheDockerBook_sample.pdf
.. _Code examples: http://www.dockerbook.com/code/index.html
.. _O'Reilly Docker cookbook: http://sebgoa.blogspot.com/2015/01/oreilly-docker-cookbook.html
.. _how2dock/docbook: https://github.com/how2dock/docbook
.. _Welcome to the Docker User Guide: http://docs.docker.com/userguide/
.. _Understanding Docker: http://docs.docker.com/introduction/understanding-docker/#so-how-does-docker-work
.. _Network Configuration: http://docs.docker.com/articles/networking/#configuring-dns
.. _Docker Compose: https://docs.docker.com/compose/
.. _How to Use Docker on OS X\: The Missing Guide: http://viget.com/extend/how-to-use-docker-on-os-x-the-missing-guide


.. _dockerinproduction:

Why Docker?
"""""""""""

    + `Sailing Past Dependency Hell With Docker`_, by Alex Johnson, July 2, 2015

.. _Sailing Past Dependency Hell With Docker: http://deis.com/blog/2015/sailing-past-dependency-hell-with-docker


Architecture
""""""""""""

+ `Docker vs. VMs? Combining Both for Cloud Portability Nirvana`_, by Thorsten von Eicken, September 2, 2014
+ `Understand the architecture`_ (v1.10), Docker web site
+ `Higher Order Infrastructure - Microservices on the Docker Swarm`_, by Nicola Paolucci, GOTO 2016

.. _Docker vs. VMs? Combining Both for Cloud Portability Nirvana: http://www.rightscale.com/blog/cloud-management-best-practices/docker-vs-vms-combining-both-cloud-portability-nirvana
.. _Understand the architecture: https://docs.docker.com/v1.10/introduction/understanding-docker/
.. _Higher Order Infrastructure - Microservices on the Docker Swarm: https://youtu.be/eQ-XMDzuvxY


Docker in Production
""""""""""""""""""""

    + `Why Docker is Not Yet Succeeding Widely in Production`_, by Simon Hørup Eskildsen, July 2015
    + `The Realities of Docker in Production`_, by Ben Ball, March 31, 2015
    + `Docker in Production`_, by Jérôme Petazzoni, September 22, 2014
    + `Docker deployments`_, by Paul Showalter & Karl Matthias, New Relic, September 10, 2014
        + GitHub `6si/shipwright`_ (The right way to build, tag and ship Docker containers.)
        + GitHub `newrelic/centurion`_ (A mass deployment tool for Docker fleets)
        + GitHub `newrelic/check_docker`_ (A Go `Nagios`_ check for Docker)
        + GitHub `newrelic/go_nagios`_ (Go lang package for writing Nagios checks)

.. _Why Docker is Not Yet Succeeding Widely in Production: http://sirupsen.com/production-docker/
.. _The Realities of Docker in Production: http://blog.heavybit.com/blog/2015/3/23/dockermeetup
.. _Docker in Production: https://youtu.be/Glk5d5WP6MI
.. _Docker deployments: https://youtu.be/2CwtJlJYmW4
.. _6si/shipwright: https://github.com/6si/shipwright/
.. _newrelic/centurion: https://github.com/newrelic/centurion
.. _newrelic/check_docker: https://github.com/newrelic/check_docker
.. _newrelic/go_nagios: https://github.com/newrelic/go_nagios
.. _Nagios: http://www.nagios.org/


.. _dockerdevelopment:

Docker and Development
""""""""""""""""""""""

    + `How To Cook Microservices (with Ruby spices)`_ is a continuously updated collection of
       notes, insights and ideas about building software platforms empowered by microservices
       architecture with Ruby language
    + `Docker for Developers`_, by Jérôme Petazzoni, November 25, 2014
    + `Tips for running Docker in development`_, by Philip Kallberg, May 27, 2015
    + GitHub `wsargent/docker-cheat-sheet`_ (Docker Cheat Sheet)
    + `Test, Develop, Build, Stage with Docker`_, by Simone Di Maulo, May 2, 2015
    + `A Docker Dev Environment in 24 Hours! (Part 1 of 2)`_, by John Fiedler, October 31, 2013
    + `A Docker Dev Environment in 24 Hours! (Part 2 of 2)`_, by John Fiedler, November 5, 2013
        + GitHub `relateiq/docker_public`_ (Instant RelateIQ Development Environment - code from parts 1 and 2)
    + `Top 10 Open-Source Docker Developer Tools`_, by Lucas Carlson, March 5, 2014
    + `Executable Images - How to Dockerize Your Development Machine`_, by Quinten Krijger, August 29, 2015
    + `Development Environments with Vagrant, Docker, and Supervisord`_, by Tyler H.T. Cipriani, May 25, 2014

.. _How To Cook Microservices (with Ruby spices): http://howtocookmicroservices.com
.. _Docker for Developers: https://youtu.be/FdkNAjjO5yQ
.. _Tips for running Docker in development: http://blog.cloud66.com/tips-for-running-docker-in-development/
.. _wsargent/docker-cheat-sheet: https://github.com/wsargent/docker-cheat-sheet
.. _Test, Develop, Build, Stage with Docker: http://toretto.me/posts/2015/05/02/Test-Develop-Build-Stage-with-Docker.html
.. _A Docker Dev Environment in 24 Hours! (Part 1 of 2): http://blog.relateiq.com/a-docker-dev-environment-in-24-hours-part-1-of-2/
.. _A Docker Dev Environment in 24 Hours! (Part 2 of 2): http://blog.relateiq.com/a-docker-dev-environment-in-24-hours-part-2-of-2/
.. _relateiq/docker_public: https://github.com/relateiq/docker_public
.. _Top 10 Open-Source Docker Developer Tools: http://www.centurylinklabs.com/top-10-open-source-docker-developer-tools/
.. _Executable Images - How to Dockerize Your Development Machine: http://www.infoq.com/articles/docker-executable-images
.. _Development Environments with Vagrant, Docker, and Supervisord: https://tylercipriani.com/2014/05/25/lightweight-portable-vagrant-docker.html


.. _dockersecurity:

Docker and Security
"""""""""""""""""""

    + `Docker Security`_, Docker web site
    + `Docker Ramps Up Container Security`_, by Jack M. Germain, May 13, 2016
    + `Understanding and Hardening Linux Containers`_ (PDF), NCC Group whitepaper by Aaron Grattafiori, April 20, 2016
       + `Docker and High Security Microservices: A Summary of Aaron Grattafiori's DockerCon 2016 Talk`_, by Daniel Bryant on August 14, 2016
    + `Containing and Attack with Linux Containers`_ (PDF), Shmoocon 2016 `presentation by Jay Beale`_, InGuardians, January 17, 2016
    + `Using Linux Containers to Jail Programs`_, by Jay Beale, Raleigh B-Sides, October 9, 2015
    + GitHub `docker/docker-bench-security`_ (The Docker Bench for Security is a script that checks for all the automatable tests included in the CIS Docker 1.6 Benchmark.  https://dockerbench.com)
    + `Introducing a *Super* Privileged Container Concept`_, by rhatdan, November 6, 2014
    + `Are Docker containers really secure?`_, by Daniel J Walsh, July 22, 2014
    + `Bringing new security features to Docker`_, by Daniel J Walsh, September 3, 2014
    + `Someone said that 30% of the images on the Docker Registry contain vulnerabilities`_, by jpetazzo, May 27, 2015
    + `Exploring Docker Volumes for Phases of Development`_, by Alan Kent, May 31, 2015
    + `Understanding Docker Security and Best Practices`_, Docker blog, May 5, 2015
    + `Container Security: Just The Good Parts`_, by Trevor Jay, April 29, 2015
    + `Docker SELinux Experimentation with Reduced Pain`_, by zwischenzugs, April 29, 2015
    + `The sad state of sysadmin in the age of containers`_, by Erich Shubert [pointing out some **extremely** poor security practices by many in DevOps]
        + `reddit.com/r/programming comments thread`_

    + `Docker security gets thumbs-up despite containers' rapid rise`_, by Toby Wolpe, ZDNet News, January 12, 2015
    + `Docker security in the future`_, by Daniel J Walsh, March 19, 2015
    + `Docker Security: Best Practices for your Vessel and Containers`_, by Michael Boelen, January 22, 2015
    + GitHub `GDSSecurity/Docker-Secure-Deployment-Guidelines`_ (Deployment checklist for securely deploying Docker)
    + `CoreOS vs. Project Atomic: A Review`_, Major Hayden, May 13, 2014
    + `Analysis of Docker Security`_, by Than Bui
    + `Storage Concepts in Docker: Persistent Storage`_, by Mark Lamourine, October 10, 2014 [Has a good discussion of SELinux labeling of directories for use by Docker containers]
    + `Docker's just a bit dodgy, but ready for rollout says Gartner`_, by Simon Sharwood
    + `Snappy Security`_
    + `Launch secure LXC containers on Fedora 20 using SELinux and sVirt`_, by Major Hayden
    + See also the :ref:`selinuxapparmorgrsecurity` section

.. _Docker Security: https://docs.docker.com/articles/security/
.. _Docker Ramps Up Container Security: http://www.ecommercetimes.com/story/cloud-computing/83493.html
.. _Understanding and Hardening Linux Containers: https://www.nccgroup.trust/globalassets/our-research/us/whitepapers/2016/april/ncc_group_understanding_hardening_linux_containers-10pdf/
.. _Docker and High Security Microservices\: A Summary of Aaron Grattafiori's DockerCon 2016 Talk: https://www.infoq.com/news/2016/08/secure-docker-microservices
.. _Using Linux Containers to Jail Programs: http://inguardians.com/bsides-containers.pdf
.. _Containing and Attack with Linux Containers: http://www.inguardians.com/2016-Shmoocon-LinuxContainers.pdf
.. _presentation by Jay Beale: http://www.securitytube.net/video/15724
.. _docker/docker-bench-security: https://github.com/docker/docker-bench-security
.. _Introducing a *Super* Privileged Container Concept: http://developers.redhat.com/blog/2014/11/06/introducing-a-super-privileged-container-concept/
.. _Are Docker containers really secure?: https://opensource.com/business/14/7/docker-security-selinux
.. _Bringing new security features to Docker: https://opensource.com/business/14/9/security-for-docker
.. _Someone said that 30% of the images on the Docker Registry contain vulnerabilities: http://jpetazzo.github.io/2015/05/27/docker-images-vulnerabilities/
.. _Understanding Docker Security and Best Practices: http://blog.docker.com/2015/05/understanding-docker-security-and-best-practices/
.. _Container Security\: Just The Good Parts: https://securityblog.redhat.com/2015/04/29/container-security-just-the-good-parts/
.. _Docker SELinux Experimentation with Reduced Pain: https://zwischenzugs.wordpress.com/2015/04/29/docker-selinux-experimentation-with-reduced-pain/
.. _The sad state of sysadmin in the age of containers: http://www.vitavonni.de/blog/201503/2015031201-the-sad-state-of-sysadmin-in-the-age-of-containers.html
.. _reddit.com/r/programming comments thread: http://www.reddit.com/r/programming/comments/33ktc9/the_sad_state_of_sysadmin_in_the_age_of_containers/
.. _Docker security gets thumbs-up despite containers' rapid rise: http://www.zdnet.com/article/docker-security-gets-thumbs-up-despite-containers-rapid-rise/
.. _Docker security in the future: https://opensource.com/business/15/3/docker-security-future
.. _Docker Security\: Best Practices for your Vessel and Containers: http://linux-audit.com/docker-security-best-practices-for-your-vessel-and-containers/
.. _GDSSecurity/Docker-Secure-Deployment-Guidelines: https://github.com/GDSSecurity/Docker-Secure-Deployment-Guidelines
.. _CoreOS vs. Project Atomic\: A Review: https://major.io/2014/05/13/coreos-vs-project-atomic-a-review/
.. _Analysis of Docker Security: http://arxiv.org/pdf/1501.02967.pdf
.. _Storage Concepts in Docker\: Persistent Storage: http://cloud-mechanic.blogspot.com/2014/10/storage-concepts-in-docker-persistent.html
.. _Docker's just a bit dodgy, but ready for rollout says Gartner: http://www.theregister.co.uk/2015/01/12/docker_security_immature_but_not_scary_says_gartner/
.. _Snappy Security: https://penguindroppings.wordpress.com/2014/12/10/snappy-security/
.. _Launch secure LXC containers on Fedora 20 using SELinux and sVirt: https://major.io/2014/04/21/launch-secure-lxc-containers-on-fedora-20-using-selinux-and-svirt/


.. _dockerorchestration:

Orchestration
"""""""""""""

    + Docker Orchestration workshop - Jérôme Petazzoni, Feb 21, 2016
        + `Part 1`_ (1:21:09)
        + `Part 2`_ (0:59:37)
        + `Parts 3 and 4`_ (3:20:54)
        + GitHub `jpetazzo/orchestration-workshop`_ (Slides and examples for the workshop)
    + `Docker Orchestration & Metrics`_, Tiffany Jernigan, Seattle Docker Meetup, December 2016
        + `Slides from Tiffany's presentation`_
    + `Docker 1.12 Swarm Mode Deep Dive Part 2: Orchestration`_, YouTube by Andrea Luzzardi, July 28, 2016
    + `Create a swarm cluster with Docker 1.12 swarm mode`_, by Luc, July 5, 2016
    + `ContainerPilot and the Autopilot Pattern`_, by Tim Gross, Container Summit Austin, July 19, 2016
    + `3 Node Swarm Cluster in 30 seconds (Docker 1.12)`_, by John Zaccone, July 29, 2016
    + Apollo
        + `Capgemini Apollo: An Open Source Microservice and Big Data Platform`_, by Daniel Bryant, June 6, 2015
        + GitHub `Capgemini/Apollo`_, An open-source platform for cloud native applications based on Apache Mesos and Docker. http://capgemini.github.io/devops/apollo/")
        + `How Apollo Uses Weave and Weave Scope`_, by Graham Taylor, June 30, 2015

    + `Atlassian Orchestration with Docker: multi-host support for the win!`_, by Nicola Paolucci, December 16, 2015
    + `DockerCon EU: Keynote on Orchestration (Docker Machine, Swarm, Compose)`_
    + `Docker 101: Dockerizing Your Infrastructure`_, by Stanley Lewis
    + `Docker and Maestro for fun, development and profit`_, by Maxime Petazzoni
    + `Docker Containers and Kubernetes with Brian Dorsey`_, YouTube, December 23, 2014
    + `CoreOS Meetup: etcd and Kubernetes`_, YouTube, March 19, 2015
    + `Docker orchestration with maestro-ng`_, by heisel
    + GitHub `signalfuse/maestro-ng`_ (Orchestration of Docker-based, multi-host environments http://www.signalfuse.com)
        + GitHub `signalfx/maestro-base`_ (Base Docker image for Maestro-enabled components http://www.signalfuse.com)
        + GitHub `WIZARD-CXY/docker-cassandra`_ (Docker image for Cassandra (Maestro orchestration))
        + GitHub `iantruslove/docker-elasticsearch`_ (Docker image for ElasticSearch (Maestro orchestration))
        + GitHub `signalfx/docker-zookeeper`_ (Docker image for ZooKeeper (Maestro orchestration) http://www.signalfuse.com)
        + GitHub `signalfx/docker-kafka`_ (Docker image for Kafka (Maestro orchestration) http://www.signalfuse.com)

    + (See also `A production ready Docker workflow. Part 3: Orchestration tools`_)
    + `Getting Started with CoreOS and Docker using Vagrant`_, by Luke Bond
    + `Deploying Docker Containers on a Vagrant CoreOS Cluster with fleet`_, by Luke Bond
    + `Vessel`_ automates the setup & use of dockerized development environments

.. _Part 1: https://youtu.be/E4b9ZfxVrss
.. _Part 2: https://youtu.be/TyTKjdp0cC0
.. _Parts 3 and 4: https://youtu.be/IJ-JXxkCxGc
.. _jpetazzo/orchestration-workshop: https://github.com/jpetazzo/orchestration-workshop
.. _Docker Orchestration & Metrics: https://vimeo.com/196638063
.. _Slides from Tiffany's presentation: https://tiffanyfj.github.io/docker-orchestration-metrics/#1
.. _Docker 1.12 Swarm Mode Deep Dive Part 2\: Orchestration: https://youtu.be/_F6PSP-qhdA
.. _Create a swarm cluster with Docker 1.12 swarm mode: http://lucjuggery.com/blog/?p=566
.. _ContainerPilot and the Autopilot Pattern: http://containersummit.io/city-series/2016/austin/videos/containerpilot-and-the-autopilot-pattern
.. _3 Node Swarm Cluster in 30 seconds (Docker 1.12): http://www.johnzaccone.io/3-node-cluster-in-30-seconds/
.. _Capgemini Apollo\: An Open Source Microservice and Big Data Platform: http://www.infoq.com/news/2015/06/capgemini-apollo
.. _Capgemini/Apollo: https://github.com/Capgemini/Apollo
.. _How Apollo Uses Weave and Weave Scope: http://capgemini.github.io/devops/how-apollo-uses-weave/
.. _Atlassian Orchestration with Docker\: multi-host support for the win!: https://developer.atlassian.com/blog/2015/12/atlassian-docker-orchestration/
.. _DockerCon EU\: Keynote on Orchestration (Docker Machine, Swarm, Compose): https://youtu.be/sGWQ8WiGN8Y
.. _Docker 101\: Dockerizing Your Infrastructure: https://youtu.be/4W2YY-qBla0
.. _Docker and Maestro for fun, development and profit: http://www.slideshare.net/MaximePetazzoni/docker-and-maestro-for-fun-development-and-profit
.. _Docker Containers and Kubernetes with Brian Dorsey: https://youtu.be/Fcb4aoSAZ98
.. _CoreOS Meetup\: etcd and Kubernetes: https://youtu.be/-9IX_c9fyGc
.. _Docker orchestration with maestro-ng: http://techblog.kabbage.com/post/115791606957/docker-orchestration-with-maestro-ng
.. _signalfuse/maestro-ng: https://github.com/signalfuse/maestro-ng
.. _signalfx/maestro-base: https://github.com/signalfx/maestro-base
.. _WIZARD-CXY/docker-cassandra: https://github.com/WIZARD-CXY/docker-cassandra
.. _iantruslove/docker-elasticsearch: https://github.com/iantruslove/docker-elasticsearch
.. _signalfx/docker-zookeeper: https://github.com/signalfx/docker-zookeeper
.. _signalfx/docker-kafka: https://github.com/signalfx/docker-kafka
.. _Getting Started with CoreOS and Docker using Vagrant: http://lukebond.ghost.io/getting-started-with-coreos-and-docker-using-vagrant/
.. _Deploying Docker Containers on a Vagrant CoreOS Cluster with fleet: https://lukebond.ghost.io/deploying-docker-containers-on-a-coreos-cluster-with-fleet/
.. _Vessel: http://awvessel.github.io


.. _dockerprivateregistry:

Using a private registry
""""""""""""""""""""""""

    + `Docker Registry`_, Docker web site
    + `Deploying a registry server`_, Docker web site
    + `Running Secured Docker Registry 2.0`_, by Jaroslav Holub, April 28, 2015
    + `How To Set Up a Private Docker Registry on Ubuntu 14.04`_, by Nik van der Ploeg, October 15, 2014
    + `How to Secure Your Private Docker Registry`_, by Alex Welch, January 2, 2015 (goes with previous post)
    + `Setup Your Own Docker Registry on CoreOS`_, Vultr, May 7, 2015
    + `Setting Up Docker Private Registry`_, by beingasysadmin, January 14, 2015
    + `Docker: How to Use Your Own Private Registry`_, Twitter University, November 12, 2013

.. _Docker Registry: https://docs.docker.com/registry/
.. _Deploying a registry server: https://docs.docker.com/registry/deploying/
.. _Running Secured Docker Registry 2.0: http://container-solutions.com/2015/04/running-secured-docker-registry-2-0/
.. _How To Set Up a Private Docker Registry on Ubuntu 14.04: https://www.digitalocean.com/community/tutorials/how-to-set-up-a-private-docker-registry-on-ubuntu-14-04
.. _How to Secure Your Private Docker Registry: http://www.centurylinklabs.com/tutorials/how-to-secure-your-private-docker-registry/
.. _Setup Your Own Docker Registry on CoreOS: https://www.vultr.com/docs/setup-your-own-docker-registry-on-coreos
.. _Setting Up Docker Private Registry: https://beingasysadmin.wordpress.com/2015/01/14/setting-up-docker-private-registry/
.. _Docker\: How to Use Your Own Private Registry: https://youtu.be/CAewZCBT4PI


.. _dockersevicediscovery:

Configuration management and service discovery
""""""""""""""""""""""""""""""""""""""""""""""
    + `Demystifying Service Discovery under Docker Engine 1.12.0`_, by ajeetraina, July 27, 2016
    + `Consul`_ ("Service discovery and configuration made easy. Distributed, highly available, and datacenter aware.")
    + `Consul Part 1: Service discovery, the easy way`_, YouTube video by OpsForce, July 17, 2016
    + `Consul Part 2: Service health and templates`_, YouTube video by OpsForce, August 3, 2016
    + `Configuration management with Consul`_, by Michael de Jong, October 26, 2015
    + `Configuration management from Git to Consul`_, by Ryan Breen, May 8, 2015
        + GitHub `Cimpress-MCP/git2consul`_ ("Mirrors the contents of a git repository into Consul KVs.")
        + GitHub `Cimpress-MCP/fsconsul`_ ("Write Consul K/Vs to the filesystem.")
        + GitHUb `Cimpress-MCP/gosecret`_ ("A Go library for encrypting and decrypting slices of byte arrays.")
    + `Distributed Configuration Management and Dark Launching Using Consul`_, by Bill Monkman, November 26, 2014 (Has examples of creating configuration management kv store)
    + GitHub `kelseyhightower/confd`_ ("Manage local application configuration files using templates and data from etcd or consul")
    + `An Introduction to Using Consul, a Service Discovery System, on Ubuntu 14.04`_ (Part 1 of 3), by Justin Ellingwood, August 15, 2014
    + `How to Configure Consul in a Production Environment on Ubuntu 14.04`_ (Part 2 of 3), by Justin Ellingwood, August 15, 2014
    + `How To Secure Consul with TLS Encryption on Ubuntu 14.04`_ (Part 3 of 3), by Justin Ellingwood, August 15, 2014
    + `Understanding Modern Service Discovery with Docker`_, by Jeff Lindsay
    + `Consul Service Discovery with Docker`_, by Jeff Lindsay
    + `Automatic Docker Service Announcement with Registrator`_, by Jeff Lindsay
    + `A High Available Docker Container Platform Using CoreOS And Consul`_, by Mark van Holsteijn
    + GitHub `democracyworks/consul-coreos`_ ("Bootstraps a Consul cluster on CoreOS using fleet and etcd")
    + `Simulating service discovery with Docker and etcd`_, by Aaditya Talwai
    + GitHub `Cimpress-MCP/git2consul`_ ("Mirrors the contents of a git repository into Consul KVs.")
    + GitHub `ianbytchek/docker-coreos-ansible-toolbox`_ ("Using Ansible with CoreOS? Use CoreOS Ansible toolbox!")

.. _Demystifying Service Discovery under Docker Engine 1.12.0: http://collabnix.com/archives/1504
.. _Consul: https://www.consul.io
.. _Consul Part 1\: Service discovery, the easy way: https://youtu.be/xyU8v5RO_kQ
.. _Consul Part 2\: Service health and templates: https://youtu.be/KgTtQnXrnMk
.. _Configuration management with Consul: https://labs.magnet.me/nerds/2015/10/26/consultant-configuration-management-with-consul.html
.. _Configuration management from Git to Consul: http://lifeinvistaprint.com/techblog/configuration-management-git-consul/
.. _Cimpress-MCP/git2consul: https://github.com/Cimpress-MCP/git2consul
.. _Cimpress-MCP/fsconsul: https://github.com/Cimpress-MCP/fsconsul
.. _Cimpress-MCP/gosecret: https://github.com/Cimpress-MCP/gosecret
.. _Distributed Configuration Management and Dark Launching Using Consul: http://code.hootsuite.com/distributed-configuration-management-and-dark-launching-using-consul/
.. _kelseyhightower/confd: https://github.com/kelseyhightower/confd
.. _An Introduction to Using Consul, a Service Discovery System, on Ubuntu 14.04: https://www.digitalocean.com/community/tutorials/an-introduction-to-using-consul-a-service-discovery-system-on-ubuntu-14-04
.. _How to Configure Consul in a Production Environment on Ubuntu 14.04: https://www.digitalocean.com/community/tutorials/how-to-configure-consul-in-a-production-environment-on-ubuntu-14-04
.. _How To Secure Consul with TLS Encryption on Ubuntu 14.04: https://www.digitalocean.com/community/tutorials/how-to-secure-consul-with-tls-encryption-on-ubuntu-14-04
.. _Understanding Modern Service Discovery with Docker: http://progrium.com/blog/2014/07/29/understanding-modern-service-discovery-with-docker/
.. _Consul Service Discovery with Docker: http://progrium.com/blog/2014/08/20/consul-service-discovery-with-docker/
.. _Automatic Docker Service Announcement with Registrator: http://progrium.com/blog/2014/09/10/automatic-docker-service-announcement-with-registrator/
.. _A High Available Docker Container Platform Using CoreOS And Consul: http://blog.xebia.com/2015/03/24/a-high-available-docker-container-platform-using-coreos-and-consul/
.. _democracyworks/consul-coreos: https://github.com/democracyworks/consul-coreos
.. _Simulating service discovery with Docker and etcd: http://talwai.github.io/#/blog/post/discovery
.. _Cimpress-MCP/git2consul: https://github.com/Cimpress-MCP/git2consul
.. _ianbytchek/docker-coreos-ansible-toolbox: https://github.com/ianbytchek/docker-coreos-ansible-toolbox


.. _dockernetworking:

Networking and Docker containers
""""""""""""""""""""""""""""""""

    + Docker native networking
        + `Docker Stacks and Attachable networks`_, by Alex Ellis, February 17, 2017
        + `Docker 1.12 Swarm Mode Deep Dive Part 1: Topology`_, YouTube by Andrea Luzzardi, July 28, 2016
        + `Splendors and Miseries of Docker Network`_, by Aleksandr Tarasov, November 16, 2015
        + `Add Docker Machine to Swarm cluster after creation`_, stackoverflow thread, January 4, 2016
        + `Docker Networking takes a step in the right direction`_, Docker blog, April 30, 2015

    + Weave
        + GitHub `weaveworks/weave`_ ("Simple, resilient multi-host Docker networking http://weave.works")
        + `Multi-host Docker deployment with Swarm and Compose using Weave 0.11`_, by errordeveloper, May 27, 2015
        + `Networking Docker Containers with Weave on CoreOS`_, Weave web site
        + `Using Weave Scope Standalone to Visualize and Monitor Docker Containers`_, Weave web site
        + `Using Docker Machine and Swarm with Weave 0.10`_, by errordeveloper, May 6, 2015
        + `How to set up networking between Docker containers`_, by Dan Nanni, March 20, 2015
        + `Using Docker Machine with Weave 0.10`_, by Ilya Dmitrichenko, April 22, 2015
            + GitHub `infrabricks/powerstrip-demo`_ (This is a TLS powerstrip weave demo, installed with docker-machine!)

        + `Elasticsearch, Weave and Docker`_, by errordeveloper, January 20, 2015
            + GitHub `errordeveloper/weave-demos/hello-apps/elasticsearch-js/scripts/run_elasticsearch_2_clusters.sh`_
            + `Curator: Tending your time-series indices`_, by Aaron Mildenstein, January 20, 2014
                + GitHub `elastic/curator`_ (Curator: Tending your Elasticsearch indices")
            + `Logstash how to remove old logs`_, by Andriy Podanenko

        + `Deploying and migrating an Elasticsearch-Logstash-Kibana stack using Docker Part 1`_, by Ryan Wallner, January 12, 2016
        + `Deploying and migrating an Elasticsearch-Logstash-Kibana stack using Docker Part 2`_, by Ryan Wallner, January 12, 2016
        + `I just created a Cassandra cluster that spans 3 different network domains, by using 2 simple shell commands. How cool is that?`_, by Yaron Rosenbaum, October 8, 2014
        + `Running a Weave Network on CoreOS`_, by errordeveloper, October 28, 2014
        + `How to Network Docker Containers with Weave`_, by Benjamin Ball, September 14, 2014
        + `Getting Started with Weave and Docker on CoreOS`_ (GitHub `fintanr/weavegs`_)
        + `Docker, Weave, Raspberry Pi and a bit of Networked Cloud Computing!`_, by Alexander Grendel, December 9, 2014

    + Pipework
        + GitHub `jpetazzo/pipework`_ (Software-Defined Networking tools for LXC (LinuX Containers))
        + `Advanced Docker Networking with Pipework`_, by Sam Leathers

    + Flannel
        + `CoreOS + Layer Meetup 10/6/14: Brian "Redbeard" Harrington - Warming Up With Flannel`_, YouTube, October 7, 2014
        + `Docker Networking - CoreOS Flannel`_, Sreenivas Makam, January 18, 2015

    + OpenVPN
        + `How To Run OpenVPN in a Docker Container on Ubuntu 14.04`_, by Kyle Manna, February 2, 2015
        + `Start an OpenVPN Container as a systemd managed service under CoreOS`_, by c-garcia, March 15, 2015
        + `OpenVPN in a container`_, by Ed Vielmetti, November 20, 2015
        + `Securing wifi traffic with OpenVPN and Docker`_, by Christopher Bunn,  April 03, 2015
        + `Docker + Joyent + OpenVPN = Bliss`_, by Jérôme Petazzoni, September 10, 2013
            + GitHub `jpetazzo/dockvpn`_ ("Recipe to build an OpenVPN image for Docker")

    + `Integrating Proxy With Docker Swarm (Tour Around Docker 1.12 Series)`_, by Viktor Farcic, August 1, 2016 [Good networking diagrams]
    + `Docker networking overview`_, by Filip Verloy, February 17, 2016
    + `Docker Swarm and experimental multihost networking with docker-machine and boot2docker`_, by IIkka Anttonen, July 15, 2015
    + `Three Solutions to Bi-directional Linking Problem in Docker Compose`_, by Abdelrahman Hosny, July 1, 2015
    + `Docker Networking Meetup - Intro to Weave/Flannel`_, by Dhananjay 'DJ' Sampath, January 23, 2015
    + `5 ways Docker is fixing its networking woes`_, by Serdar Yegulalp, October 20, 2014
    + `Docker networking - IP per container, one /24 per pod(worker)`_, by Vicente De Luca, April 30, 2015
    + See also: `Network Configuration`_

.. _Docker Stacks and Attachable networks: http://blog.alexellis.io/docker-stacks-attachable-networks/
.. _Docker 1.12 Swarm Mode Deep Dive Part 1\: Topology: https://youtu.be/dooPhkXT9yI
.. _Splendors and Miseries of Docker Network: http://developerblog.info/2015/11/16/splendors-and-miseries-of-docker-network/
.. _Add Docker Machine to Swarm cluster after creation: http://stackoverflow.com/questions/34601718/add-docker-machine-to-swarm-cluster-after-creation
.. _Docker Networking takes a step in the right direction: http://blog.docker.com/2015/04/docker-networking-takes-a-step-in-the-right-direction-2/
.. _weaveworks/weave: https://github.com/weaveworks/weave#installation
.. _Multi-host Docker deployment with Swarm and Compose using Weave 0.11: http://blog.weave.works/2015/05/27/multi-host-docker-deployment-with-swarm-and-compose-using-weave-0-11/
.. _Networking Docker Containers with Weave on CoreOS: http://weave.works/guides/weave-docker-coreos-simple.html
.. _Using Weave Scope Standalone to Visualize and Monitor Docker Containers: http://weave.works/guides/weave-scope/weave-scope-alone-monitor-containers.html
.. _Using Docker Machine with Weave 0.10: http://weaveblog.com/2015/04/22/using-docker-machine-with-weave-0-10/
.. _How to set up networking between Docker containers: http://xmodulo.com/networking-between-docker-containers.html
.. _Using Docker Machine and Swarm with Weave 0.10: http://blog.weave.works/2015/05/06/using-docker-machine-and-swarm-with-weave-0-10/
.. _infrabricks/powerstrip-demo: https://github.com/infrabricks/powerstrip-demo
.. _Elasticsearch, Weave and Docker: http://weaveblog.com/2015/01/20/elasticsearch-and-weave/
.. _errordeveloper/weave-demos/hello-apps/elasticsearch-js/scripts/run_elasticsearch_2_clusters.sh: https://github.com/errordeveloper/weave-demos/blob/d2c2a00/hello-apps/elasticsearch-js/scripts/run_elasticsearch_2_clusters.sh
.. _Curator\: Tending your time-series indices: https://www.elastic.co/blog/curator-tending-your-time-series-indices
.. _elastic/curator: https://github.com/elastic/curator
.. _Logstash how to remove old logs: http://druler.com/node/884
.. _Deploying and migrating an Elasticsearch-Logstash-Kibana stack using Docker Part 1: https://clusterhq.com/2016/01/12/a-single-node-elk-flocker/
.. _Deploying and migrating an Elasticsearch-Logstash-Kibana stack using Docker Part 2: https://clusterhq.com/2016/01/12/b-multinode-elk-flocker/
.. _I just created a Cassandra cluster that spans 3 different network domains, by using 2 simple shell commands. How cool is that?: http://blog.weave.works/2014/10/08/i-just-created-a-cassandra-cluster-that-spans-3-different-network-domains-by-using-2-simple-shell-commands-how-cool-is-that/
.. _Running a Weave Network on CoreOS: http://weaveblog.com/2014/10/28/running-a-weave-network-on-coreos/
.. _How to Network Docker Containers with Weave: http://java.dzone.com/articles/how-network-docker-containers
.. _Getting Started with Weave and Docker on CoreOS: https://github.com/fintanr/weave-gs/tree/master/coreos-simple
.. _Docker, Weave, Raspberry Pi and a bit of Networked Cloud Computing!: https://medium.com/@ALGrendel/docker-weave-a-little-cloud-and-a-raspberry-pi-381f73a4376d
.. _jpetazzo/pipework: https://github.com/jpetazzo/pipework
.. _Advanced Docker Networking with Pipework: https://opsbot.com/advanced-docker-networking-pipework/
.. _CoreOS + Layer Meetup 10/6/14\: Brian "Redbeard" Harrington - Warming Up With Flannel: https://youtu.be/uC8Y_TGtwPo
.. _Docker Networking - CoreOS Flannel: https://sreeninet.wordpress.com/2015/01/18/docker-networking-coreos-flannel/
.. _How To Run OpenVPN in a Docker Container on Ubuntu 14.04: https://www.digitalocean.com/community/tutorials/how-to-run-openvpn-in-a-docker-container-on-ubuntu-14-04
.. _Start an OpenVPN Container as a systemd managed service under CoreOS: https://www.snip2code.com/Snippet/407394/Start-an-OpenVPN-Container-as-a-systemd-
.. _OpenVPN in a container: http://vielmetti.github.io/post/2015/2015-11-20-openvpn-in-a-container/
.. _Securing wifi traffic with OpenVPN and Docker: http://bunn.cc/2015/openvpn-with-docker/
.. _Docker + Joyent + OpenVPN = Bliss: https://blog.docker.com/2013/09/docker-joyent-openvpn-bliss/
.. _jpetazzo/dockvpn: https://github.com/jpetazzo/dockvpn
.. _Docker networking overview: http://filipv.net/2016/02/17/docker-networking-overview/
.. _Integrating Proxy With Docker Swarm (Tour Around Docker 1.12 Series): https://technologyconversations.com/2016/08/01/integrating-proxy-with-docker-swarm-tour-around-docker-1-12-series/
.. _Docker Swarm and experimental multihost networking with docker-machine and boot2docker: http://sirile.github.io/2015/07/15/docker-swarm-and-experimental-multihost-networking-with-docker-machine-and-boot2docker.html
.. _Three Solutions to Bi-directional Linking Problem in Docker Compose: http://abdelrahmanhosny.com/2015/07/01/3-solutions-to-bi-directional-linking-problem-in-docker-compose/
.. _Docker Networking Meetup - Intro to Weave/Flannel: http://www.slideshare.net/dsampath1/dockernetworking-meetup-intro-to-weaveflannel
.. _5 ways Docker is fixing its networking woes: http://www.infoworld.com/article/2835222/application-virtualization/5-ways-docker-is-fixing-its-networking-woes.html
.. _Docker networking - IP per container, one /24 per pod(worker): http://www.nethero.org/post/117792763407/docker-networking-ip-per-container-one-24-per


.. _dockerpersistentstorage:

Persistent storage in Docker containers
"""""""""""""""""""""""""""""""""""""""

    + `Docker: Storage Patterns for Persistence`_, by Karim Vaes, February 11, 2016
    + `Comprehensive Overview of Storage Scalability in Docker`_, by Jeremy Eder, September 30, 2014
    + `Storage Concepts in Docker: Shared Storage and the VOLUME directive`_, by Mark Lamourine, October 7, 2014
    + `Storage Concepts in Docker: Persistent Storage`_, by Mark Lamourine, October 10, 2014 [Has a good discussion of SELinux labeling of directories for use by Docker containers]
    + `Share disks through NFS on a CoreOS cluster?`_, stackexchange post, November 25, 2014
    + `Enabling and Mounting NFS on CoreOS`_, by Scott Lowe, February 20, 2015
    + `Exploring Docker Volumes for Phases of Development`_, by Alan Kent, May 31, 2015
    + `Quickly build arbitrary size Hadoop Cluster based on Docker`_, by KiwenLau, May 29, 2015
    + See also: Hadoop section of :ref:`databasetools`

.. _Docker\: Storage Patterns for Persistence: https://kvaes.wordpress.com/2016/02/11/docker-storage-patterns-for-persistence/
.. _Comprehensive Overview of Storage Scalability in Docker: https://developerblog.redhat.com/2014/09/30/overview-storage-scalability-docker/
.. _Storage Concepts in Docker\: Shared Storage and the VOLUME directive: http://cloud-mechanic.blogspot.com/2014/10/storage-concepts-in-docker.html
.. _Share disks through NFS on a CoreOS cluster?: http://serverfault.com/questions/647014/share-disks-through-nfs-on-a-coreos-cluster?rq=1
.. _Enabling and Mounting NFS on CoreOS: http://blog.scottlowe.org/2015/02/20/config-mount-nfs-coreos/
.. _Exploring Docker Volumes for Phases of Development: https://alankent.wordpress.com/2015/05/31/exploring-docker-volumes-for-phases-of-development/
.. _Quickly build arbitrary size Hadoop Cluster based on Docker: http://kiwenlau.blogspot.com/2015/05/quickly-build-arbitrary-size-hadoop.html


.. _dockerpersistentservices:

Persistent services within Docker containers
""""""""""""""""""""""""""""""""""""""""""""

    + `Automatically start containers`_, Docker web site
    + `Introducing dumb-init, an init system for Docker containers`_, by Chris K., Jan 6, 2016
    + `Docker All The Things: Nginx And Supervisor`_, by Matthew McKeen, December 14, 2013
    + `Running node and nginx in docker with supervisor`_, stackoverflow post, December 2, 2014
    + `Creating a Docker Container to run PHP, NGINX and Hip Hop VM (HHVM)`_, July 15, 2014
    + `Roll your own Docker registry with Docker, Compose, Supervisor, and Nginx`_, by Philipp Wintermantel, March 18, 2014

.. _Automatically start containers: https://docs.docker.com/engine/admin/host_integration/
.. _Introducing dumb-init, an init system for Docker containers: http://engineeringblog.yelp.com/2016/01/dumb-init-an-init-for-docker.html
.. _Docker All The Things\: Nginx And Supervisor: http://mmckeen.net/blog/2013/12/14/docker-all-the-things-nginx-and-supervisor/
.. _Running node and nginx in docker with supervisor: http://stackoverflow.com/questions/27249380/running-node-and-nginx-in-docker-with-supervisor
.. _Creating a Docker Container to run PHP, NGINX and Hip Hop VM (HHVM): http://blog.seeddigital.co/post/91801062414/creating-a-docker-container-to-run-php-nginx-and
.. _Roll your own Docker registry with Docker, Compose, Supervisor, and Nginx: http://www.kf-interactive.com/blog/roll-your-own-docker-registry-with-docker-compose-supervisor-and-nginx/


.. _dockerclustering:

Clustering Docker containers
""""""""""""""""""""""""""""

    + `Using Docker Stack And Compose YAML Files To Deploy Swarm Services`_, by Viktor Farcic, January 23, 2017
    + `Running a Small Docker Swarm Cluster`_, Scott Lowe, March 6, 2015
    + `Docker Machine, Compose & Swarm`_, by MediaGlasses
    + `Clustering Using Docker Swarm 0.2.0`_, by Arun Gupta
    + `A quick overview of Docker Swarm`_, by Olivier Robert, February 2, 2016

.. _Using Docker Stack And Compose YAML Files To Deploy Swarm Services: https://technologyconversations.com/2017/01/23/using-docker-stack-and-compose-yaml-files-to-deploy-swarm-services/
.. _Running a Small Docker Swarm Cluster: http://blog.scottlowe.org/2015/03/06/running-own-docker-swarm-cluster/
.. _Docker Machine, Compose & Swarm: https://media-glass.es/2015/03/21/docker-machine-compose-swarm/
.. _Clustering Using Docker Swarm 0.2.0: https://www.voxxed.com/blog/2015/04/clustering-using-docker-swarm-0-2-0/
.. _A quick overview of Docker Swarm: http://blog.agilepartner.net/docker-swarm/


.. _dockerlogging:

Logging/monitoring activity of containers
"""""""""""""""""""""""""""""""""""""""""

    + `Collecting All Docker Logs with Fluentd`_, by Kiyoto Tamura, July 7, 2015
    + `Automating Docker Logging: ElasticSearch, Logstash, Kibana, and Logspout`_, by Nathan LeClaire, April 27, 2015
    + `Running High Performance and Fault Tolerant Elasticsearch Clusters on Docker`_, sematext group, November 24, 2015
    + `Scalable Docker Monitoring with Fluentd, Elasticsearch and Kibana 4`_, by manu, November 21, 2014
    + `Performance tuning ELK stack`_, by Josh Reichardt, March 30, 2015
    + `syslog logging driver for Docker`_, by Mark Wolfe, May 3, 2015
    + `Real-time monitoring of Hadoop clusters`_, by Attila Kanto, October 7, 2014
        + `Apache Hadoop 2.6.0 on Docker`_, by Janos Matyas, September 15, 2014

.. _Collecting All Docker Logs with Fluentd: http://blog.treasuredata.com/blog/2015/07/07/collecting-docker-logs-with-fluentd
.. _Automating Docker Logging\: ElasticSearch, Logstash, Kibana, and Logspout: http://nathanleclaire.com/blog/2015/04/27/automating-docker-logging-elasticsearch-logstash-kibana-and-logspout/
.. _Running High Performance and Fault Tolerant Elasticsearch Clusters on Docker: http://www.slideshare.net/sematext/running-highperformance-and-fault-tolerant-elasticsearch-clusters-on-docker
.. _Scalable Docker Monitoring with Fluentd, Elasticsearch and Kibana 4: http://blog.snapdragon.cc/2014/11/21/scalable-docker-monitoring-fluentd-elasticsearch-kibana-4/
.. _Performance tuning ELK stack: http://thepracticalsysadmin.com/performance-tuning-elk-stack/
.. _syslog logging driver for Docker: http://www.wolfe.id.au/2015/05/03/syslog-logging-driver-for-docker/
.. _Real-time monitoring of Hadoop clusters: http://blog.sequenceiq.com/blog/2014/10/07/hadoop-monitoring/
.. _Apache Hadoop 2.6.0 on Docker: http://blog.sequenceiq.com/blog/2014/12/02/hadoop-2-6-0-docker/


.. _dockercleanup:

Cleaning up (or keeping Docker images as small as possible)
"""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

    + `Reducing the size of Docker Images`_, by Richard Woudenberg, March 18, 2015
    + `Making Debian Docker Images Smaller`_, by Dave Beckett, April 18, 2015
    + `How I shrunk a Docker image by 98.8% – featuring fanotify`_, by Jean-Tiare LE BIGOT, April 25, 2015
    + `Low on disk space, cleaning up old Docker containers`_, by johnarce, May 20, 2014
    + `Squashing Docker Images`_, by Jason Wilder, August 19, 2014
    + `Optimizing Docker Images`_, by Brian DeHamer, July 28, 2014
    + `Create The Smallest Possible Docker Container`_, by Adriaan de Jonge, July 4, 2014
    + `How To Create The Smallest Possible Docker Container Of Any Image`_, by Mark van Holsteijn, June 30, 2015

.. _Reducing the size of Docker Images: http://woudenberg.io/reducing-docker-image-size/
.. _Making Debian Docker Images Smaller: https://www.dajobe.org/blog/2015/04/18/making-debian-docker-images-smaller/
.. _How I shrunk a Docker image by 98.8% – featuring fanotify: https://blog.jtlebi.fr/2015/04/25/how-i-shrunk-a-docker-image-by-98-8-featuring-fanotify/
.. _Low on disk space, cleaning up old Docker containers: https://meta.discourse.org/t/low-on-disk-space-cleaning-up-old-docker-containers/15792
.. _Squashing Docker Images: http://jasonwilder.com/blog/2014/08/19/squashing-docker-images/
.. _Optimizing Docker Images: https://labs.ctl.io/optimizing-docker-images/
.. _Create The Smallest Possible Docker Container: http://blog.xebia.com/2014/07/04/create-the-smallest-possible-docker-container/
.. _How To Create The Smallest Possible Docker Container Of Any Image: http://blog.xebia.com/2015/06/30/how-to-create-the-smallest-possible-docker-container-of-any-image


.. _dockerandci:

Docker and Continuous Integration
"""""""""""""""""""""""""""""""""

    + `Docker Jenkins`_, by Yuri Kushch, February 17, 2017
    + `Easy CD-CI with Jenkins, Docker Swarm and Docker secrets`_, by KrazY CoCoon Lab, March 6, 2017
    + `Fully automated development environment with docker-compose`_, by Andrew Orsich, February 22, 2017
    + `Continuous Integration, Delivery or Deployment with Jenkins, Docker and Ansible`_ by Viktor Farcic, February 11, 2015
    + `Deployment Pipeline using Docker, Jenkins, Java and Couchbase`_, by Arun Gupta, September 9, 2016
    + Scaling to Infinity with Docker Swarm, Docker Compose and Consul, by Viktor Farcic, July 2, 2015
        + `(Part 1/4) - A Taste of What is to Come`_
        + `(Part 2/4) - Manually Deploying Services`_
        + `(Part 3/4) - Blue-Green Deployment, Automation and Self-Healing Procedure`_
        + `(Part 4/4) - Scaling Individual Services`_

    + `Putting Jenkins in a Docker Container`_, by Maxfield F. Stewart, Riot Games Engineering blog
        + GitHub `maxfields2000/dockerjenkins_tutorial`_ ("A repository for items learned in my Getting Started with Jenkins and Docker tutorial series")

    + `Delivering eBay’s CI Solution with Apache Mesos – Part I`_, by The eBay PaaS Team, April 4, 2014
    + `Delivering eBay’s CI Solution with Apache Mesos – Part II`_, by The eBay PaaS Team, May 12, 2014
    + `DockerCon Video: Delivering eBay’s CI Solution with Apache Mesos & Docker`_, by Victor Coisne, June 23, 2014
    + `Disaster-proofing slaves with Docker Swarm and the CloudBees Jenkins Platform`_, by Tracy Kennedy, June 19, 2015
    + `Continuous Integration and Delivery with Docker`_, by Jaroslav Holub, May 28, 2015
    + `Jenkins`_, Docker Hub (Official Jenkins Docker Image)
    + `Running Jenkins in Docker Containers`_, by Peter Sellers, February 11, 2015
    + `Import Jenkins Configuration to a dockerized jenkins`_, by Allan Espinoza, January 25, 2015
    + `Docker in Docker with Jenkins and Supervisord`_, by Johan Haleby, March 14, 2015
    + `Jenkins in a Docker container`_, by by Thomas Einwaller, September 1, 2014

.. _Docker Jenkins: http://ykushch.net/docker-jenkins/
.. _Easy CD-CI with Jenkins, Docker Swarm and Docker secrets: https://www.youtube.com/watch?v=USxRrMWzK1s
.. _Fully automated development environment with docker-compose: https://blog.maqpie.com/2017/02/22/fully-automated-development-environment-with-docker-compose/
.. _Continuous Integration, Delivery or Deployment with Jenkins, Docker and Ansible: http://technologyconversations.com/2015/02/11/continuous-integration-delivery-or-deployment-with-jenkins-docker-and-ansible/
.. _Deployment Pipeline using Docker, Jenkins, Java and Couchbase: http://blog.couchbase.com/2016/september/deployment-pipeline-docker-jenkins-java-couchbase
.. _(Part 1/4) - A Taste of What is to Come: http://technologyconversations.com/2015/07/02/scaling-to-infinity-with-docker-swarm-docker-compose-and-consul-part-14-a-taste-of-what-is-to-come
.. _(Part 2/4) - Manually Deploying Services: http://technologyconversations.com/2015/07/02/scaling-to-infinity-with-docker-swarm-docker-compose-and-consul-part-24-manually-deploying-services/
.. _(Part 3/4) - Blue-Green Deployment, Automation and Self-Healing Procedure: http://technologyconversations.com/2015/07/02/scaling-to-infinity-with-docker-swarm-docker-compose-and-consul-part-34-blue-green-deployment-automation-and-self-healing-procedure/
.. _(Part 4/4) - Scaling Individual Services: http://technologyconversations.com/2015/07/02/scaling-to-infinity-with-docker-swarm-docker-compose-and-consul-part-44-scaling-individual-services/
.. _Putting Jenkins in a Docker Container: http://engineering.riotgames.com/news/putting-jenkins-docker-container
.. _maxfields2000/dockerjenkins_tutorial: https://github.com/maxfields2000/dockerjenkins_tutorial
.. _Delivering eBay’s CI Solution with Apache Mesos – Part I: http://www.ebaytechblog.com/2014/04/04/delivering-ebays-ci-solution-with-apache-mesos-part-i/
.. _Delivering eBay’s CI Solution with Apache Mesos – Part II: http://www.ebaytechblog.com/2014/05/12/delivering-ebays-ci-solution-with-apache-mesos-part-ii/
.. _DockerCon Video\: Delivering eBay’s CI Solution with Apache Mesos & Docker: https://blog.docker.com/2014/06/dockercon-video-delivering-ebays-ci-solution-with-apache-mesos-docker/
.. _Disaster-proofing slaves with Docker Swarm and the CloudBees Jenkins Platform: http://blog.cloudbees.com/2015/06/disaster-proofing-slaves-with-docker.html
.. _Continuous Integration and Delivery with Docker: http://blog.codeship.com/continuous-integration-and-delivery-with-docker/
.. _Jenkins: https://registry.hub.docker.com/_/jenkins/
.. _Running Jenkins in Docker Containers: http://www.catosplace.net/blog/2015/02/11/running-jenkins-in-docker-containers/
.. _Import Jenkins Configuration to a dockerized jenkins: http://qiita.com/aespinosa/items/051652966abe84200810
.. _Docker in Docker with Jenkins and Supervisord: http://www.jayway.com/2015/03/14/docker-in-docker-with-jenkins-and-supervisord/
.. _Jenkins in a Docker container: http://dertompson.com/2014/09/01/jenkins-in-a-docker-container/

.. _dockermisc:

Miscellaneous Docker related articles and blog posts
""""""""""""""""""""""""""""""""""""""""""""""""""""

+ `Consul Template for transparent load balancing of containers`_, by Jose Luis Ordiales, April 1, 2015
+ `Orchestrating your containers with CoreOS, an introduction`_, by Jose Luis Ordiales, July 12, 2015
+ `3 hours to Docker fundamentals: Jumpstart your Docker knowledge`_, by Aater Suleman, October 13, 2014
+ Docker Registry `richhaase/bigtop-hadoop`_
+ `Automated docker ambassadors with CoreOS + registrator + ambassadord`_
+ `Understanding user file ownership in docker: how to avoid changing permissions of linked volumes`_, stackoverflow
+ GitHub `signalfx/docker-java`_ (Java Docker API Client)
+ `A production ready Docker workflow`_ (part 1), by Luis Elizondo
+ `A production ready Docker workflow. Part 2: The Storage Problem`_, by Luis Elizondo
+ `A production ready Docker workflow. Part 3: Orchestration tools`_, by Luis Elizondo
+ `Your very own server with Docker`_, by Erwyn
+ `A Not Very Short Introduction to Docker`_, by Anders Janmyr
+ `Deploying NGINX and NGINX Plus with Docker`_, by Rick Nelson
+ `Make Docker Machine Do Anything With Our Experimental Extensions`_, by kcoleman, September 26, 2015
+ `Consul + Consul-Template with Docker-Compose`_, by Neil Ni, September 14, 2015
+ `Virtualenv the Docker way`_, by Justyna Ilczuk, Nov 16, 2014
+ GitHub `daniel-illi/docker-haproxy-letsencrypt`_ ("Dockerized HAProxy with Let's Encrypt integration")
+ GitHub `BradJonesLLC/docker-nginx-letsencrypt`_ ("Nginx container with Let's Encrypt auto-renew ")

.. _Consul Template for transparent load balancing of containers: http://jlordiales.me/2015/04/01/consul-template/
.. _Orchestrating your containers with CoreOS, an introduction: http://jlordiales.me/2015/07/12/coreos/
.. _3 hours to Docker fundamentals\: Jumpstart your Docker knowledge: https://youtu.be/ddhU3NMrhX4
.. _richhaase/bigtop-hadoop: https://registry.hub.docker.com/u/richhaase/bigtop-hadoop/dockerfile/
.. _Automated docker ambassadors with CoreOS + registrator + ambassadord: http://www.virtualroadside.com/blog/index.php/2014/07/28/automated-docker-ambassadors-with-coreos-registrator-ambassadord/
.. _Understanding user file ownership in docker\: how to avoid changing permissions of linked volumes: http://stackoverflow.com/questions/26500270/understanding-user-file-ownership-in-docker-how-to-avoid-changing-permissions-o
.. _signalfx/docker-java: https://github.com/signalfx
.. _A production ready Docker workflow: http://www.luiselizondo.net/a-production-ready-docker-workflow/
.. _A production ready Docker workflow. Part 2\: The Storage Problem: http://www.luiselizondo.net/a-production-ready-docker-workflow-part-2-the-storage-problem/
.. _A production ready Docker workflow. Part 3\: Orchestration tools: http://www.luiselizondo.net/a-production-ready-docker-workflow-part-3-orchestration-tools/
.. _Your very own server with Docker: http://erwyn.piwany.com/your-very-own-server-with-docker/
.. _A Not Very Short Introduction to Docker: http://anders.janmyr.com/2015/03/a-not-very-short-introduction-to-docker.html
.. _Deploying NGINX and NGINX Plus with Docker: http://nginx.com/blog/deploying-nginx-nginx-plus-docker/
.. _Make Docker Machine Do Anything With Our Experimental Extensions: http://blog.emccode.com/2015/09/26/make-docker-machine-do-anything-with-our-experimental-extensions/?_tmc=HOoesHjhTxGK1ObYvbHhezREYxiu004TYVsEyUyuLa8
.. _Consul + Consul-Template with Docker-Compose: http://blog.neilni.com/2015/09/14/consul-and-consul-template-with-docker-compose/
.. _Virtualenv the Docker way: http://tinystruggles.com/2014/11/16/docker-virtualenv.html
.. _daniel-illi/docker-haproxy-letsencrypt: https://github.com/daniel-illi/docker-haproxy-letsencrypt/tree/rock-on
.. _BradJonesLLC/docker-nginx-letsencrypt: https://github.com/BradJonesLLC/docker-nginx-letsencrypt


Operating systems for running Docker
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

CoreOS
""""""

+ `CoreOS`_
    + `Container Overview`_, CoreOS web site
    + `CoreOS Clustering`_, CoreOS web site
    + `CoreOS Cluster Architectures`_, CoreOS web site
    + `CoreOS Overview and Current Status`_, Slideshare by Sreenivas Makam, April 17, 2016
    + `etcd`_, CoreOS web site
    + `Running CoreOS on Vagrant`_, CoreOS web site
    + `Booting CoreOS via PXE`_, CoreOS web site
        + GitHub `kelseyhightower/coreos-ipxe-server`_ ("CoreOS iPXE server")
    + `Customizing Docker`_, CoreOS web site

    + `Deploying a Service Using fleet`_ CoreOS web site
    + `Installing CoreOS to Disk`_, CoreOS web site
        + GitHub `nyarla/coreos-live-iso/makeiso.sh`_
    + `Ignition: Better Machine Configuration (CoreOS Fest 2015)`_, May 27, 2015 (has some details of boot sequence that are hard to learn)
    + `Lessons Learned From Building Platforms on Top of CoreOS (CoreOS Fest 2015)`_, May 27, 2015
        + `10 Lessons Learned Using CoreOS`_, by Gabriel Monroy (slides for CoreOS Fest 2015 talk)

+ Pay attention to these bug reports (and what is said in them)
    + `Network settings should be set in oem cloud-config.yml`_ (coreos/bugs #11, April 28, 2014)
    + `custom iptables - boot order`_, (coreos/bugs #58, June 26, 2014)
    + `docker-tcp.socket fails: Socket service docker.service already active, refusing.`_ (coreos/coreos-vagrant bug #172, September 30, 2014)
    + `How does docker-tcp.socket actually enable Docker's remote API on CoreOS?`_, superuser post, January 5, 2015

+ `How can I customize bashrc, bash_profile or profile on a CoreOS installation?`_, Stackoverflow post by Richard, Jun 2 2015
+ GitHub https://github.com/coreos/coreos-overlay/tree/master/app-shells/bash/files/
+ `CoreOS: Orchestrating the Fleet`_, YouTube video by Brian Waldon, July 8, 2014
+ Digital Ocean tutorial series: Getting Started with CoreOS
    + `How To Troubleshoot Common Issues with your CoreOS Servers`_, (part 8 of 9), September 18, 2015
    + `How To Secure Your CoreOS Cluster with TLS/SSL and Firewall Rules`_, (part 9 of 9), December 7, 2015


.. _CoreOS: https://coreos.com
.. (Container Overview was already defined above)
.. _CoreOS Clustering: https://coreos.com/using-coreos/clustering/
.. _CoreOS Cluster Architectures: https://coreos.com/docs/cluster-management/setup/cluster-architectures/
.. _CoreOS Overview and Current Status: http://www.slideshare.net/SreenivasMakam/coreos-overview-and-current-status
.. _etcd: https://coreos.com/using-coreos/etcd/
.. _Running CoreOS on Vagrant: https://coreos.com/docs/running-coreos/platforms/vagrant/#single-machine
.. _Booting CoreOS via PXE: https://coreos.com/docs/running-coreos/bare-metal/booting-with-pxe/
.. _kelseyhightower/coreos-ipxe-server: https://github.com/kelseyhightower/coreos-ipxe-server
.. _Customizing Docker: https://coreos.com/os/docs/latest/customizating-docker.html
.. _Deploying a Service Using fleet: https://coreos.com/docs/launching-containers/launching/fleet-example-deployment/
.. _Installing CoreOS to Disk: https://coreos.com/os/docs/latest/installing-to-disk.html
.. _nyarla/coreos-live-iso/makeiso.sh: https://github.com/nyarla/coreos-live-iso/blob/master/makeiso.sh#L66
.. _Ignition\: Better Machine Configuration (CoreOS Fest 2015): https://www.youtube.com/watch?v=ly3uwn0HzBI
.. _Lessons Learned From Building Platforms on Top of CoreOS (CoreOS Fest 2015): https://www.youtube.com/watch?v=yCWhnLlFvhI
.. _10 Lessons Learned Using CoreOS: https://gabrtv.github.io/10-lessons-learned-using-coreos/
.. _Network settings should be set in oem cloud-config.yml: https://github.com/coreos/bugs/issues/11
.. _docker-tcp.socket fails\: Socket service docker.service already active, refusing.: https://github.com/coreos/coreos-vagrant/issues/172
.. _custom iptables - boot order: https://github.com/coreos/bugs/issues/58
.. _How does docker-tcp.socket actually enable Docker's remote API on CoreOS?: https://superuser.com/questions/860869/how-does-docker-tcp-socket-actually-enable-dockers-remote-api-on-coreos
.. _How can I customize bashrc, bash_profile or profile on a CoreOS installation?: http://stackoverflow.com/questions/30596866/how-can-i-customize-bashrc-bash-profile-or-profile-on-a-coreos-installation
.. _CoreOS\: Orchestrating the Fleet: https://youtu.be/jWeAJOQIjDM
.. _How To Troubleshoot Common Issues with your CoreOS Servers: https://www.digitalocean.com/community/tutorials/how-to-troubleshoot-common-issues-with-your-coreos-servers
.. _How To Secure Your CoreOS Cluster with TLS/SSL and Firewall Rules: https://www.digitalocean.com/community/tutorials/how-to-secure-your-coreos-cluster-with-tls-ssl-and-firewall-rules


OpenNode OS
"""""""""""

+ `OpenNode OS`_ ("Lightweight bare-metal cloud OS combining Linux Containers and KVM
  full virtualization options into payload optimized solution.")
+ `NodeFabric Host Image`_ ("NodeFabric delivers hyperconverged database and storage solution
  for highly available, self-healing and load-balanced cloud services")

.. _OpenNode OS: http://opennodecloud.com/products/opennode-os.html
.. _NodeFabric Host Image: http://opennodecloud.com/products/nodefabric.html



RancherOS
"""""""""

+ `RancherOS`_ (A minimalist distribution of Linux designed from the ground up to run Docker containers.)
+ `Announcing RancherOS`_

.. _RancherOS: http://rancher.com/rancher-os/
.. _Announcing RancherOS: http://rancher.com/announcing-rancher-os/


Project Atomic
""""""""""""""

+ `Project Atomic`_ (Trusted Distributions, Atomic Updates)

.. _Project Atomic: http://www.projectatomic.io


Ubuntu "Snappy"
"""""""""""""""

+ `Snappy Ubuntu Core`_
    + `SNAPPY UBUNTU CORE image for Raspberry Pi`_

+ `It's a Snap!`_
+ `Snappy Security`_

.. _Snappy Ubuntu Core: http://developer.ubuntu.com/en/snappy/
.. _SNAPPY UBUNTU CORE image for Raspberry Pi: http://downloads.raspberrypi.org/ubuntu_latest
.. _It's a Snap!: http://blog.dustinkirkland.com/2014/12/its-a-snap.html
.. (Snappy Security was already defined above)


ArchLinux
"""""""""

+ `ArchLinux`_

.. _ArchLinux: https://www.archlinux.org


.. _configurationmanagent:

Configuration management and automated provisioning
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+ `Collins`_ ("Infrastructure management for engineers")
+ GitHub `coreos/etcd`_ (A highly-available key value store for shared configuration and service discovery)
    + `Brandon Philips Explains etcd`_, by Phil Whelan
    + `CoreOS: etcd 2.0`_, by Brandon Philips

+ `The Marriage of Ansible and Docker`_, by Zuletzt geändert von Unbekannter Benutzer, June 5, 2015
+ `docker, ansible and vagrant`_, by Wojtek Oledzki, January 1, 2015
+ `Ubuntu Cloud-Init Technology`_, YouTube video by ubuntucloud, December 8, 2010
+ `The Assimilation Project`_
+ `Ansible and Docker`_, by Ash Wilson
+ `OpenStack`_
    + `Building HA Clusters with Ansible and Openstack`_, by Remy van Elst, July 25, 2014
        + GitHub `RaymiiOrg/ansible`_ (ansible/openstack-example)
    + `Automating Openstack with cloud init run a script on VM's first boot`_, by Remy van Elst, March 11, 2015
    + `Provisioning IaaS Clouds with Dynamic Ansible Inventories and OpenStack Metadata`_, by Lukas Pustina
    + GitHub `ewindisch/dockenstack`_ (OpenStack Devstack on Docker)
    + `OpenStack: Docker wiki section`_ from OpenStack
    + `OpenStack is overkill for Docker: New tooling is necessary for effectively managing Docker at scale`_, by Matt Asay, August 10, 2015
    + `Up and Running with Docker Machine and OpenStack`_, by Spencer Smith, Solinea blog, July 8, 2015
    + `OpenStackClient and OpenStack Python SDK`_, youtube video by Dean Troyer, October 27, 2015
    + `Life Without DevStack: OpenStack Development With OSA`_, by Miguel Grinberg
        + `(Demonstration video)`_

+ `Agile Configuration Management – Intermezzo`_ by Marcus Philip, Diabol
+ `Top 5 Open Source Linux Server Provisioning Software`_, by NIXCRAFT

.. _Collins: http://tumblr.github.io/collins/index.html
.. _coreos/etcd: https://github.com/coreos/etcd
.. _Brandon Philips Explains etcd: http://www.activestate.com/blog/2014/03/brandon-philips-explains-etcd
.. _CoreOS\: etcd 2.0: https://youtu.be/z6tjawXZ71E
.. _The Marriage of Ansible and Docker: https://bildung.xarif.de/xwiki/bin/Articles/The+Marriage+of+Ansible+and+Docker
.. _docker, ansible and vagrant: http://hoborglabs.com/en/blog/2014/docker-and-ansible
.. _Ubuntu Cloud-Init Technology: https://youtu.be/-zL3BdbKyGY
.. _The Assimilation Project: http://linux-ha.org/source-doc/assimilation/html/index.html
.. _Ansible and Docker: https://developer.rackspace.com/blog/ansible-and-docker/
.. _OpenStack: http://www.openstack.org
.. _Building HA Clusters with Ansible and Openstack: https://raymii.org/s/articles/Building_HA_Clusters_With_Ansible_and_Openstack.html
.. _RaymiiOrg/ansible: https://github.com/RaymiiOrg/ansible/tree/master/openstack-example
.. _Automating Openstack with cloud init run a script on VM's first boot: https://raymii.org/s/tutorials/Automating_Openstack_with_Cloud_init_run_a_script_on_VMs_first_boot.html
.. _Provisioning IaaS Clouds with Dynamic Ansible Inventories and OpenStack Metadata: https://blog.codecentric.de/en/2014/06/provisioning-iaas-clouds-dynamic-ansible-inventories-openstack-metadata/
.. _ewindisch/dockenstack: https://github.com/ewindisch/dockenstack
.. _OpenStack\: Docker wiki section: https://wiki.openstack.org/wiki/Docker
.. _OpenStack is overkill for Docker\: New tooling is necessary for effectively managing Docker at scale: http://www.techrepublic.com/article/openstack-is-overkill-for-docker/
.. _Up and Running with Docker Machine and OpenStack: http://www.solinea.com/blog/up-and-running-with-docker-machine-and-openstack
.. _OpenStackClient and OpenStack Python SDK: https://www.youtube.com/watch?v=D-4Avtxjby0
.. _Life Without DevStack\: OpenStack Development With OSA: https://www.openstack.org/assets/Uploads/Life-Without-DevStack-OpenStack-Development-With-OSA-1-.pdf
.. _(Demonstration video): https://asciinema.org/a/28461
.. _Agile Configuration Management – Intermezzo: http://blog.diabol.se/?p=773
.. _Top 5 Open Source Linux Server Provisioning Software: http://www.cyberciti.biz/tips/server-provisioning-software.html



.. _virtualbox:

Virtualbox
~~~~~~~~~~

+ `Virtual Box Headless Cheatsheet: Headless Virtual Machine Install/Import and setup`_, by Tim Arneaud, October 9, 2012

.. _Virtual Box Headless Cheatsheet\: Headless Virtual Machine Install/Import and setup: http://it-ovid.blogspot.com/2012/10/virtual-box-headless-cheatsheet.html


.. _secpacker:

Packer
~~~~~~

+ `Packer`_
    + `Command Line: Build`_
    + `Debugging Packer Builds`_
+ GitHub `boxcutter/ubuntu`_ ("Virtual machine templates for Ubuntu")
+ GitHub `tylert/packer-build`_ ("Packer Automated VM Image and Vagrant Box Builds")
+ `Packer: In 10 minutes, from zero to bootable VirtualBox Ubuntu 12.04`_, by @kappataumu, September 8, 2013


.. _Packer: https://www.packer.io/
.. _Command Line\: Build: https://www.packer.io/docs/command-line/build.html
.. _Debugging Packer Builds: https://www.packer.io/docs/other/debugging.html
.. _boxcutter/ubuntu: https://github.com/boxcutter/ubuntu
.. _tylert/packer-build: https://github.com/tylert/packer-build
.. _Packer\: In 10 minutes, from zero to bootable VirtualBox Ubuntu 12.04:  http://kappataumu.com/articles/creating-an-Ubuntu-VM-with-packer.html



.. _secvagrant:

Vagrant
~~~~~~~

+ `Vagrant`_
+ `How To Use Vagrant To Create Small Virtual Test Lab on a Linux / OS X / MS-Windows`_
+ `How to Create and Share a Vagrant Base Box`_, by George Fekete, July 17, 2014
+ `Vagrantfile Explained: Setting Up and Provisioning with Shell`_, by George Fekete, July 19, 2014
+ `Multi-Machine`_ environment documentation from Hashicorp
+ `Using Vagrant and Ansible`_, Ansible documentation
+ `Change Insecure Key To My Own Key On Vagrant`_, by ermaker, November 18, 2015
+ GitHub `AAFC-MBB/vagrant-specify7`_ ("Package to launch a Specify7 instance in a Vagrant VM")
+ `IP lookup for Vagrant private networking`_, by wamonite, July 12, 2014
+ `Elegant virtualization with Vagrant`_, by zenonharley, July 21, 2015

.. _Vagrant: https://www.vagrantup.com/
.. _How To Use Vagrant To Create Small Virtual Test Lab on a Linux / OS X / MS-Windows: http://www.cyberciti.biz/cloud-computing/use-vagrant-to-create-small-virtual-lab-on-linux-osx/
.. _How to Create and Share a Vagrant Base Box: http://www.sitepoint.com/create-share-vagrant-base-box/
.. _Vagrantfile Explained\: Setting Up and Provisioning with Shell: http://www.sitepoint.com/vagrantfile-explained-setting-provisioning-shell/
.. _Multi-Machine: https://docs.vagrantup.com/v2/multi-machine/
.. _Using Vagrant and Ansible: http://docs.ansible.com/ansible/guide_vagrant.html
.. _Change Insecure Key To My Own Key On Vagrant: https://ermaker.github.io/blog/2015/11/18/change-insecure-key-to-my-own-key-on-vagrant.html
.. _AAFC-MBB/vagrant-specify7: https://github.com/AAFC-MBB/vagrant-specify7
.. _IP lookup for Vagrant private networking: http://www.wamonite.com/ip-lookup-for-vagrant-private-networking.html
.. _Elegant virtualization with Vagrant: http://zenonharley.com/virtualbox/lamp/2015/07/21/elegant-virtualization-with-vagrant.html


.. _secansible:

Ansible
~~~~~~~

+ `Ansible`_ (web site)
    + `Playbooks Best Practices`_
    + GitHub `ansible/ansible-examples`_ ("A few starter examples of ansible playbooks, to show features and how they work together. See http://galaxy.ansible.com for example roles from the Ansible community for deploying many popular applications.")
    + `docker - manage docker containers`_

+ Alternate "Best Practices" (possibly conflicting, but helpful to consider none the less)
    + `Laying out roles, inventories and playbooks`_, by Michel Blanc, July 2, 2015
    + `Best practices to build great Ansible playbooks`_, by Maxime Thoonsen, October 12, 2015
    + `Ansible (Real Life) Good Practices`_, by Raphael Campardou,  March 19, 2014 (has pre-commit Git hook for ``ansbile-vault``)
    + `Lessons from using Ansible exclusively for 2 years`_, by Corban Raun, March 24, 2015
    + `6 practices for super smooth Ansible experience`_, by Maxim Chernyak, June 18, 2014
    + GitHub `enginyoyen/ansible-best-practises`_ ("A project structure that outlines some best practices of how to use ansible")
    + `More Tips and Tricks`_, slideshare by bcoca, October 11, 2016
      https://www.slideshare.net/bcoca/more-tips-n-tricks

+ `Episode #43 - 19 Minutes With Ansible (Part 1/4)`_, Justin Weissig, sysadmincasts.com, January 13, 2015
+ `Episode #45 - Learning Ansible with Vagrant (Part 2/4)`_, Justin Weissig, sysadmincasts.com, March 19, 2015
    + GitHub `jweissig/episode-45`_ ("Episode #45 - Learning Ansible with Vagrant")

+ `Episode #46 - Configuration Management with Ansible (Part 3/4)`_, Justin Weissig, sysadmincasts.com, March 26, 2015
+ `Episode #47 - Zero-downtime Deployment with Ansible (Part 4/4)`_, Justin Weissig, sysadmincasts.com, April 2, 2015
    + GitHub `jweissig/episode-47`_ ("Episode #47 - Zero-downtime Deployments with Ansible (Part 4/4)")

+ `Graduating Past Playbooks: How to Use Ansible When Your Infrastructure Grows Up`_, by Rob McQueen
    + GitHub `nylas/ansible-flask-example`_ ("Example using ansible-test and wrapper roles to implement a simple flask webapp")

+ The Fedora Project `ansible playbook/files/etc repository for fedora infrastructure`_
+ `How Twitter Uses Ansible`_, YouTube video by Ansible, May 21, 2014
+ GitHub `ePages-de/mac-dev-setup`_ ("Automated provisioning of your Apple Mac (Java) development machine using Ansible")

+ Advanced Ansible concepts, **gotchas**, things to keep in mind...
    + `Security hardening for openstack-ansible`_, Openstack web site
        + `Automated Security Hardening with OpenStack-Ansible`_, by Major Hayden, Openstack Austin Summit, May 1, 2016
        + GitHub `openstack/openstack-ansible-security`_ ("Security Role for OpenStack-Ansible http://openstack.org")

    + Templating
        + `Jinja2 for better Ansible playbooks and templates`_, by Daniel Schneller, August 25, 2014
        + `Ansible: "default" and "bool" filters`_, by dddpaul-github, November 30, 2015
        + `Ansible loop through group vars in template`_, Stackoverflow post, November 18, 2014
        + `Ansible loop over variables`_, Stackoverflow post, October 28, 2014
        + `Jinja2 Template Inheritence`_
        + `[jinja2] Help with blocks`_, Reddit /r/Ansible post by by FlowLabel

    + Dynamic Inventory
        + `Dynamic Inventory`_, Ansible documentation
        + `Adapting inventory for Ansible`_, by Jan-Piet Mens
        + `Creating custom dynamic inventories for Ansible`_, by Jeff Geerling, June 11, 2015
        + `Writing a Custom Ansible Dynamic Inventory Script`_, by Adam Johnson, December 4, 2016
        + `Using DNS as an Ansible dynamic inventory`_, by Remie Bolte, January 1, 2016

    + Facts vs. Variables
        + `Fact Caching`_ and `gathering`_, Ansible documentation
        + `Fastest way to gather facts to fact cache`_, Stackoverflow post, September 1, 2015
        + `Ansible Custom Facts`_, serverascode.com

    + Ansible Plugins
        + `Ansible module development in Python - 101`_, by Yves Fauser, Ansible Munich Meetup - going into 2016, February 23, 2016
        + `Ansible: Modules and Action Plugins`_, by Nicholas Grisey Demengel, January 20, 2015
        + `An action plugin for Ansible to handle SSH host keys and DNS SSHFP records`_, by Jan-Piet Mens, November 3, 2012
        + `v2 callback plugin migration (thread)`_, Google Groups

    + Front-ends for Ansible
        + `Ansible Tower`_
        + `DevOps Automation – Ansible+Semaphore is Indispensable!`_, by Thaddeus, code-complete.com
            + GitHub `ansible-semaphore/semaphore`_ ("Open Source Alternative to Ansible Tower https://ansible-semaphore.github.io/semaphore")
        + `Building an Automated Config Management Server using Ansible+Flask+Redis`_, by deepakmdas (beingsysadmin), April 21, 2015
        + `rundeck`_ ("Go fast. Be secure.")
        + `stackstorm`_ ("Event-Driven Automation")
            + GitHub `StackStorm/st2`_ ("StackStorm (aka "IFTTT for Ops") is event-driven automation commonly used for auto-remediation, security responses, facilitated troubleshooting, complex deployments, and more. Includes rules engine, workflow,1800+ integrations (see /st2contrib), native ChatOps and so forth."
            + `New In StackStorm: Ansible Integration`_, by Eugen C., June 5, 2015

    + Handling multi-stage or multi-deployment environments
        + `Multistage environments with Ansible`_, by Ross Tuck, May 15, 2014
        + `Multi-stage provisioning`_, by Victor Volle, Ansible Munich Meetup - going into 2016, February 23, 2016

    + `Ansible Tips and Tricks`_ on ReadTheDocs
    + `How to Use Ansible Roles to Abstract your Infrastructure Environment`_, by Justin Ellingwood, February 11, 2014
    + `Jinja2 for better Ansible playbooks and templates`_, by Daniel Schneller, August 25, 2014
    + `Ansible - some random useful things`_, by David Goodwin, August 4, 2014
    + `Tagging`_, ThinkAnsible, June 4, 2014
    + `Scalable and Understandable Provisioning with Ansible and Vagrant`_, by Julien Ponge, October 15, 2013
    + `Alejandro Guirao Rodríguez - Extending and embedding Ansible with Python`_, YouTube video from EuroPython 2015
    + `etcd + ansible = crazy delicious`_, by UnicornClouds
    + `How I Fully Automated OS X Provisioning With Ansible`_, by Daniel Jaouen
    + `Ansible tips`_, by Deni Bertović, October 13, 2014
    + `Debugging Ansible Tasks`_, by Greg Hurrell, August 7, 2015
    + GitHub `dellis23/ansible-toolkit`_ ("Ansible toolkit hopes to solve [some Ansible playbook] problems by providing some simple visibility tools.")
    + GitHub `ks888/ansible-playbook-debugger`_ ("A Debugger for Ansible Playbook")
    + `Hacking ansible`_, slideshare, October 15, 2014 ("a quick presentation on ansible internals and a focus on the ease of expansion through the plugin")
    + `ansible-exec: ansible-playbook wrapper for executing playbooks`_, by Hagai Kariti, August 26, 2014
    + `Using virtualenv Python in local Ansible`_, by Matt Behrens, April 5, 2014
    + `Ansible: A Simple Rollback Strategy for Roles and Playbooks`_, by Valentino Gagliardi, June 25, 2014
    + `Proposal for fixing playbooks with dynamic include problems`_, Ansible Development Google Group post

.. _Ansible: http://www.ansible.com/get-started
.. _Playbooks Best Practices: http://docs.ansible.com/ansible/playbooks_best_practices.html#use-dynamic-inventory-with-clouds
.. _docker - manage docker containers: http://docs.ansible.com/ansible/docker_module.html
.. _ansible/ansible-examples: https://github.com/ansible/ansible-examples
.. _Best practices to build great Ansible playbooks: https://www.theodo.fr/blog/2015/10/best-practices-to-build-great-ansible-playbooks/
.. _Laying out roles, inventories and playbooks: https://leucos.github.io/ansible-files-layout
.. _Ansible (Real Life) Good Practices: https://www.reinteractive.net/posts/167-ansible-real-life-good-practices
.. _Lessons from using Ansible exclusively for 2 years: https://blog.serverdensity.com/what-ive-learnt-from-using-ansible-exclusively-for-2-years/
.. _6 practices for super smooth Ansible experience: http://hakunin.com/six-ansible-practices
.. _enginyoyen/ansible-best-practises: https://github.com/enginyoyen/ansible-best-practises/
.. _More Tips and Tricks: https://www.slideshare.net/bcoca/more-tips-n-tricks
.. _Episode #43 - 19 Minutes With Ansible (Part 1/4): https://sysadmincasts.com/episodes/43-19-minutes-with-ansible-part-1-4
.. _Episode #45 - Learning Ansible with Vagrant (Part 2/4): https://sysadmincasts.com/episodes/45-learning-ansible-with-vagrant-part-2-4
.. _jweissig/episode-45: https://github.com/jweissig/episode-45
.. _Episode #46 - Configuration Management with Ansible (Part 3/4): https://sysadmincasts.com/episodes/46-configuration-management-with-ansible-part-3-4
.. _Episode #47 - Zero-downtime Deployment with Ansible (Part 4/4): https://sysadmincasts.com/episodes/47-zero-downtime-deployments-with-ansible-part-4-4
.. _jweissig/episode-47: https://github.com/jweissig/episode-47
.. _Graduating Past Playbooks\: How to Use Ansible When Your Infrastructure Grows Up: https://nylas.com/blog/graduating-past-playbooks
.. _nylas/ansible-flask-example: https://github.com/nylas/ansible-flask-example
.. _ansible playbook/files/etc repository for fedora infrastructure: https://infrastructure.fedoraproject.org/cgit/ansible.git
.. _How Twitter Uses Ansible: https://youtu.be/fwGrKXzocg4
.. _ePages-de/mac-dev-setup: https://github.com/ePages-de/mac-dev-setup
.. _Security hardening for openstack-ansible: http://docs.openstack.org/developer/openstack-ansible-security/
.. _Automated Security Hardening with OpenStack-Ansible: https://www.openstack.org/videos/video/automated-security-hardening-with-openstack-ansible
.. _openstack/openstack-ansible-security: https://github.com/openstack/openstack-ansible-security
.. _Jinja2 for better Ansible playbooks and templates: https://blog.codecentric.de/en/2014/08/jinja2-better-ansible-playbooks-templates/
.. _Ansible\: "default" and "bool" filters: https://dddpaul.github.io/blog/2015/11/30/ansible-default-and-bool-filters/
.. _Ansible loop through group vars in template: http://stackoverflow.com/questions/26989492/ansible-loop-through-group-vars-in-template
.. _Ansible loop over variables: http://stackoverflow.com/questions/26606121/ansible-loop-over-variables
.. _Jinja2 Template Inheritence: http://jinja.pocoo.org/docs/2.9/templates/#template-inheritance
.. _[jinja2] Help with blocks: https://www.reddit.com/r/ansible/comments/4npvpb/jinja2_help_with_blocks/
.. _Dynamic Inventory: http://docs.ansible.com/intro_dynamic_inventory.html
.. _Adapting inventory for Ansible : http://jpmens.net/2013/06/18/adapting-inventory-for-ansible/
.. _Creating custom dynamic inventories for Ansible: http://www.jeffgeerling.com/blog/creating-custom-dynamic-inventories-ansible
.. _Writing a Custom Ansible Dynamic Inventory Script: https://adamj.eu/tech/2016/12/04/writing-a-custom-ansible-dynamic-inventory-script/
.. _Using DNS as an Ansible dynamic inventory: https://medium.com/@remie/using-dns-as-an-ansible-dynamic-inventory-e65a2ed6bc9#.9r4jlndnc
.. _Fact Caching: http://docs.ansible.com/ansible/playbooks_variables.html#fact-caching
.. _gathering: http://docs.ansible.com/ansible/intro_configuration.html#gathering
.. _Fastest way to gather facts to fact cache: http://stackoverflow.com/questions/32703874/fastest-way-to-gather-facts-to-fact-cache
.. _Ansible Custom Facts: http://serverascode.com/2015/01/27/ansible-custom-facts.html
.. _Ansible module development in Python - 101: https://youtu.be/35UVffLINkc?t=31m16s
.. _Ansible\: Modules and Action Plugins: http://ndemengel.github.io/2015/01/20/ansible-modules-and-action-plugins/
.. _An action plugin for Ansible to handle SSH host keys and DNS SSHFP records: http://jpmens.net/2012/11/03/an-action-plugin-for-ansible-to-handle-ssh-host-keys/
.. _v2 callback plugin migration (thread): https://groups.google.com/d/msg/ansible-devel/DQiGednLgU0/JIvQ2Z-zFQAJ
.. _Ansible Tower: https://www.ansible.com/tower
.. _DevOps Automation – Ansible+Semaphore is Indispensable!: https://code-complete.com/code/?p=40
.. _ansible-semaphore/semaphore: https://github.com/ansible-semaphore/semaphore
.. _Building an Automated Config Management Server using Ansible+Flask+Redis: https://beingasysadmin.wordpress.com/2015/04/21/building-an-automated-config-management-server-using-ansibleflaskredis/
.. _rundeck: http://rundeck.org
.. _stackstorm: https://stackstorm.com/
.. _StackStorm/st2: https://github.com/StackStorm/st2
.. _New In StackStorm\: Ansible Integration: https://stackstorm.com/2015/06/05/new-in-stackstorm-ansible-integration/
.. _Multistage environments with Ansible: http://rosstuck.com/multistage-environments-with-ansible/
.. _Multi-stage provisioning: https://youtu.be/35UVffLINkc
.. _Ansible Tips and Tricks: https://ansible-tips-and-tricks.readthedocs.io/en/latest/
.. _How to Use Ansible Roles to Abstract your Infrastructure Environment: https://www.digitalocean.com/community/tutorials/how-to-use-ansible-roles-to-abstract-your-infrastructure-environment
.. _Jinja2 for better Ansible playbooks and templates: https://blog.codecentric.de/en/2014/08/jinja2-better-ansible-playbooks-templates/
.. _Ansible - some random useful things: https://codepoets.co.uk/2014/ansible-random-things/
.. _Tagging: http://thinkansible.com/ansible-tagging/
.. _Scalable and Understandable Provisioning with Ansible and Vagrant: https://julien.ponge.org/blog/scalable-and-understandable-provisioning-with-ansible-and-vagrant/
.. _Alejandro Guirao Rodríguez - Extending and embedding Ansible with Python: https://youtu.be/qLoBHbVb0Fw
.. _etcd + ansible = crazy delicious: http://www.unicornclouds.com/blog_posts/etcd_ansible_integration
.. _How I Fully Automated OS X Provisioning With Ansible: http://il.luminat.us/blog/2014/04/19/how-i-fully-automated-os-x-with-ansible/
.. _Ansible tips: http://goodcode.io/articles/ansible-tips/
.. _Debugging Ansible Tasks: https://wincent.com/wiki/Debugging_Ansible_tasks
.. _dellis23/ansible-toolkit: https://libraries.io/pypi/ansible-toolkit
.. _ks888/ansible-playbook-debugger: https://github.com/ks888/ansible-playbook-debugger
.. _Hacking ansible: http://www.slideshare.net/bcoca/hacking-ansible
.. _ansible-exec\: ansible-playbook wrapper for executing playbooks: https://www.bigpanda.io/blog/ansible-exec-ansible-playbook-wrapper-for-executing-playbooks
.. _Using virtualenv Python in local Ansible: https://www.zigg.com/2014/using-virtualenv-python-local-ansible.html
.. _Ansible\: A Simple Rollback Strategy for Roles and Playbooks: http://www.servermanaged.it/ansible/ansible-simple-rollback-strategy/
.. _Proposal for fixing playbooks with dynamic include problems: https://groups.google.com/forum/#!msg/ansible-devel/9aJaoVeRdOg/B4TvRTLgCAAJ


.. _secsecrets:

Storing Secrets for Development and Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+ `Managing Secrets In Docker Swarm Clusters`_, by Viktor Farcic, February 23, 2017
+ `Docker Compose v3.1 file format now supports Docker 1.13.1 Secret Management`_, by ajeetraina, February 15 2017
+ `Secrets at Scale: Automated Bootstrapping of Secrets and Identity in the Cloud`_, by Ian Haken, USENIX, January 30, 2017
+ `Ask HN: In a microservice architecture, how do you handle managing secrets?`_, HackerNews post, January 9, 2016

+ Variable separation using Ansible
    + `Variable File Separation`_, Ansible documentation
    + `How to open source provisioning script yet keep secrets secret? Is a two repository approach recommended?`_, self.ansible post by sovietmudkipz

+ Ansible Vault

    + `Safely storing Ansible playbook secrets`_, On Web Security blog, June 23, 2015
    + `Best Practices: Variables and Vaults`_, Ansible web site
    + `Ansible: Using Vault`_, video tutorial by ServersForHackers, Feb 16, 2015
    + `Managing Secrets with Ansible Vault – The Missing Guide (Part 1 of 2)`_, by Dan Tehranian, July 24, 2015
    + `Managing Secrets with Ansible Vault – The Missing Guide (Part 2 of 2)`_, by Dan Tehranian, July 24, 2015
    + `Ansible: How to encrypt some variables in an inventory file in a separate vault file?`_, Stackoverflow post by Adam Matan, May 13 2015
    + GitHub Gist `tristanfisher/Ansible-Vault how-to.md`_ ("A short tutorial on how to use Vault in your Ansible workflow. Ansible-vault allows you to more safely store sensitive information in a source code repository or on disk.")
    + `Encrypting Login Credentials in Ansible Vault`_, by Dan Tehranian, August 17, 2015

+ Hashicorp Vault

    + `Introduction to Vault`_, YouTube video by Seth Vargo, December 24, 2015
    + `Vault: A tool for managing secrets`_, by Mitchell Hashimoto, April 28, 2015
    + `2 Key-Value Stores compared - Keywhiz (Square) & Vault (Hashicorp)`_, YouTube video, June 12, 2015
    + GitHub `hashicorp/vault`_ ("A tool for managing secrets. http://vaultproject.io")
    + `Storing Secrets at Scale with HashiCorp's Vault: Q&A with Armon Dadgar`_, by Daniel Bryant, September 9, 2015
    + GitHub `jhaals/ansible-vault`_ ("ansible lookup plugin for secrets stored in Vault by HashiCorp")
    + `Managing all your secrets with Vault - Review and Walkthrough`_, by Martin Rusev, January 29, 2016

+ Consul
    + `Crypt: Store and retrieve encrypted configuration parameters from etcd or consul`_

.. _Managing Secrets In Docker Swarm Clusters: https://technologyconversations.com/2017/02/23/managing-secrets-in-docker-swarm-clusters
.. _Docker Compose v3.1 file format now supports Docker 1.13.1 Secret Management: http://collabnix.com/archives/2565
.. _Secrets at Scale\: Automated Bootstrapping of Secrets and Identity in the Cloud: https://www.usenix.org/sites/default/files/conference/protected-files/enigma_haken_slides.pdf
.. _Ask HN\: In a microservice architecture, how do you handle managing secrets?: https://news.ycombinator.com/item?id=10927043
.. _Variable File Separation: http://docs.ansible.com/ansible/playbooks_variables.html#variable-file-separation
.. _How to open source provisioning script yet keep secrets secret? Is a two repository approach recommended?: https://www.reddit.com/r/ansible/comments/5v00vh/how_to_open_source_provisioning_script_yet_keep/
.. _Safely storing Ansible playbook secrets: https://www.onwebsecurity.com/devops/safely-storing-ansible-playbook-secrets
.. _Best Practices\: Variables and Vaults: http://docs.ansible.com/ansible/playbooks_best_practices.html#variables-and-vaults
.. _Ansible\: Using Vault: https://serversforhackers.com/video/ansible-using-vault
.. _Managing Secrets with Ansible Vault – The Missing Guide (Part 1 of 2): https://dantehranian.wordpress.com/2015/07/24/managing-secrets-with-ansible-vault-the-missing-guide-part-1-of-2/
.. _Managing Secrets with Ansible Vault – The Missing Guide (Part 2 of 2): https://dantehranian.wordpress.com/2015/07/24/managing-secrets-with-ansible-vault-the-missing-guide-part-2-of-2/
.. _Ansible\: How to encrypt some variables in an inventory file in a separate vault file?: http://stackoverflow.com/questions/30209062/ansible-how-to-encrypt-some-variables-in-an-inventory-file-in-a-separate-vault
.. _tristanfisher/Ansible-Vault how-to.md: https://gist.github.com/tristanfisher/e5a306144a637dc739e7
.. _Encrypting Login Credentials in Ansible Vault: https://dantehranian.wordpress.com/2015/08/17/encrypting-login-credentials-in-ansible-vault/

.. _Introduction to Vault: https://www.youtube.com/watch?v=yvImdLP3LEA
.. _Vault\: A tool for managing secrets: https://www.hashicorp.com/blog/vault.html
.. _2 Key-Value Stores compared - Keywhiz (Square) & Vault (Hashicorp): https://www.youtube.com/watch?v=ZhmiwxYlJ7c
.. _hashicorp/vault: https://github.com/hashicorp/vault
.. _Storing Secrets at Scale with HashiCorp's Vault\: Q&A with Armon Dadgar: http://www.infoq.com/news/2015/09/hashicorp-vault
.. _jhaals/ansible-vault: https://github.com/jhaals/ansible-vault
.. _Managing all your secrets with Vault - Review and Walkthrough: https://www.amon.cx/blog/managing-all-secrets-with-vault/
.. _Crypt\: Store and retrieve encrypted configuration parameters from etcd or consul: http://xordataexchange.github.io/crypt/


.. _secterraform:

Terraform
~~~~~~~~~

+ GitHub `hashicorp/terraform`_ ("Terraform is a tool for building, changing, and combining infrastructure safely and efficiently. https://www.terraform.io/")
+ `Seth Vargo on Hashicorp Terraform`_, YouTube video by Seth Vargo, February 17, 2015
+ `Terraform Deploying Consul Cluster in One Command`_, Vimeo video from HashiCorp
+ `How To Use Terraform with DigitalOcean`_, by Mitchell Anicas, September 25, 2017
+ `Getting Started with Terraform for Digitalocean`_, by Eric Wright, January 9, 2017
+ `Terraform Infrastructure Design Patterns`_, by Bart Spaans, September 14, 2015
+ `Using Vagrant, Docker, & Terraform to streamline your development & demo environments`_, YouTube video by Nikhil Vaze, October 18, 2015
+ `Orchestrating Docker with Terraform and Consul by Mitchell Hashimoto`_, YouTube video, January 7, 2015
+ `Guide to automating a multi-tiered application securely on AWS with Docker and Terraform`_, by Greg Osuri
+ `ansible stuffs - how to securely get SSH fingerprints/public keys from newly created AWS instances`_, by Bill Cawthra, September 8, 2016

.. _hashicorp/terraform: https://github.com/hashicorp/terraform
.. _Seth Vargo on Hashicorp Terraform: https://www.youtube.com/watch?v=pKIFHtO2Y7I
.. _Terraform Deploying Consul Cluster in One Command: https://vimeo.com/108755280
.. _How To Use Terraform with DigitalOcean: https://www.digitalocean.com/community/tutorials/how-to-use-terraform-with-digitalocean
.. _Getting Started with Terraform for Digitalocean: https://turbonomic.com/blog/on-technology/getting-started-with-terraform-for-digital-ocean/
.. _Terraform Infrastructure Design Patterns: https://opencredo.com/terraform-infrastructure-design-patterns/
.. _Using Vagrant, Docker, & Terraform to streamline your development & demo environments: https://www.youtube.com/watch?v=-ANpDfvoovU&spfreload=10#t=2085.990491
.. _Orchestrating Docker with Terraform and Consul by Mitchell Hashimoto: https://www.youtube.com/watch?v=zi89DZiWfqg
.. _Guide to automating a multi-tiered application securely on AWS with Docker and Terraform: https://www.airpair.com/aws/posts/ntiered-aws-docker-terraform-guide
.. _ansible stuffs - how to securely get SSH fingerprints/public keys from newly created AWS instances: https://fullmetalhealth.com/spin-off-ansible-ssh-bastion-host-dynamic-infrastructure-aws-gathering-ssh-public-key-aws-system-log/

.. _secnomad:

Nomad
~~~~~

+ `Nomad`_, by Armon Dadgar, September 28, 2015
+ `Introduction to Nomad`_, nomadproject.io web site
+ GitHub `hashicorp/nomad`_ ("A Distributed, Highly Available, Datacenter-Aware Scheduler https://www.nomadproject.io/")

.. _Nomad: https://www.hashicorp.com/blog/nomad.html
.. _Introduction to Nomad: https://www.nomadproject.io/intro/index.html
.. _hashicorp/nomad: https://github.com/hashicorp/nomad


.. _secotto:

Otto
~~~~

+ `Otto: Development and Deployment Made Easy`_ ottoproject.io web site
+ `First look at HashiCorp's Otto`_, YouTube video by Mat Schaffer, September 29, 2015
+ `Mitchell Hashimoto - Introducing Nomad and Otto`_, YouTube video, October 27, 2015
+ `Otto: Getting Started`_, ottoproject.io web site
+ GitHub `hashicorp/otto`_ ("Development and deployment made easy. https://ottoproject.io")

.. _Otto\: Development and Deployment Made Easy: https://www.ottoproject.io/
.. _First look at HashiCorp's Otto: https://www.youtube.com/watch?v=WHt4xhX7XJc
.. _Mitchell Hashimoto - Introducing Nomad and Otto: https://www.youtube.com/watch?v=aF_HPTHtqCA
.. _Otto\: Getting Started: https://www.ottoproject.io/intro/getting-started/install.html
.. _hashicorp/otto: https://github.com/hashicorp/otto


Automated distributed system deployment options using Ansible
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+ `ansible-dims-playbooks`_ (`ansible-dims-playbooks Documenations`_)
+ `Mantl`_ (`Mantl Documentation`)_
+ `DC/OS`_
+ Intel `Trusted Analytics Platform`_
+ `Debops`_
+ The Fedora Project `ansible playbook/files/etc repository for fedora infrastructure`_

.. _ansible-dims-playbooks: https://github.com/uw-dims/ansible-dims-playbooks
.. _ansible-dims-playbooks Documenations: https://ansible-dims-playbooks.readthedocs.com
.. _Mantl: http://www.mantl.io/download
.. _Mantl documentation: http://mantl.readthedocs.io/en/latest/getting_started/index.html
.. _DC/OS: https://dcos.io/
.. _Trusted Analytics Platform: https://github.com/trustedanalytics
.. _Debops: https://debops.org/
.. This is already a reference: ansible playbook/files/etc repository for fedora infrastructure

.. _secsystemd:

Using ``systemd`` and ``upstart`` for services
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    + `Demystifying systemd: A Practical Guide`_, by Ben Breard and Lennart Poettering, Red Hat Summit, April 14-17, 2014 (PDF file)
    + `systemd for Administrators`_, eBook by psankar
    + `Systemd Essentials: Working with Services, Units, and the Journal`_, Justin Ellingwood, DigitalOcean, April 20, 2015
    + `How To Use Systemctl to Manage Systemd Services and Units`_, Justin Ellingwood, DigitalOcean, February 1, 2015
    + `Understanding Systemd Units and Unit Files`_, Justin Ellingwood, DigitalOcean, February 17, 2015
    + `How to debug Systemd problems`_, Fedora Project web site
    + `Auditing systemd: solving failed units with systemctl`_, by Michael Boelen, November 24, 2014
    + `systemd.service — Service unit configuration`_, Freedesktop.org man page
    + `Investigating systemd errors`_, ArchLinux web page
    + `SystemdForUpstartUsers`_, Ubuntu web site
    + Gist `damncabbage/unicorn.conf`_ ("I have the most terrible Upstart config for Unicorn. Support start, stop, restart and reload (rolling restart).")
    + `How can I tell upstart to restart a service when a different service is restarted?`_, by Marius Gedminas, AskUbuntu post, February 13, 2013
    + Logging
        + `Reading the System Log`_, CoreOS web site
        + `How To Use Journalctl to View and Manipulate Systemd Logs`_, Justin Ellingwood, DigitalOcean, February 5, 2015
        + GitHub `systemd/journal2gelf`_ ("Ships new systemd journal entries to a remote destination in Graylog Extended Log Format (GELF)")
        + `Sending CoreOS Logs to Loggly`_, by Garland Kan, October 27, 2015
        + `Platform logging`_, Deis
        + `Responsive infrastructure - How to setup rsyslog, elasticsearch and kibana on CoreOS and AWS (2)`_, by Simon Dittlman, April 3, 2015
        + `A UDP syslog client in Python — for Windows and UNIX`_, by Christian Stigen Larsen, December 3, 2013


.. _Demystifying systemd\: A Practical Guide: http://people.redhat.com/bbreard/presos/Summit_Demystifying_systemd.pdf
.. _systemd for Administrators: http://0pointer.de/public/systemd-ebook-psankar.pdf
.. _Systemd Essentials\: Working with Services, Units, and the Journal: https://www.digitalocean.com/community/tutorials/systemd-essentials-working-with-services-units-and-the-journal
.. _How To Use Systemctl to Manage Systemd Services and Units: https://www.digitalocean.com/community/tutorials/how-to-use-systemctl-to-manage-systemd-services-and-units
.. _Understanding Systemd Units and Unit Files: https://www.digitalocean.com/community/tutorials/understanding-systemd-units-and-unit-files
.. _How to debug Systemd problems: https://fedoraproject.org/wiki/How_to_debug_Systemd_problems
.. _Auditing systemd\: solving failed units with systemctl: http://linux-audit.com/auditing-systemd-solving-failed-units-with-systemctl/
.. _systemd.service — Service unit configuration: http://www.freedesktop.org/software/systemd/man/systemd.service.html
.. _Investigating systemd errors: https://wiki.archlinux.org/index.php/Systemd#Investigating_systemd_errors
.. _SystemdForUpstartUsers: https://wiki.ubuntu.com/SystemdForUpstartUsers
.. _damncabbage/unicorn.conf: https://gist.github.com/damncabbage/8aac0b375bdd6d1c702c
.. _How can I tell upstart to restart a service when a different service is restarted?: https://www.askubuntu.com/questions/254681/how-can-i-tell-upstart-to-restart-a-service-when-a-different-service-is-restarted
.. _Reading the System Log: https://coreos.com/os/docs/latest/reading-the-system-log.html
.. _How To Use Journalctl to View and Manipulate Systemd Logs: https://www.digitalocean.com/community/tutorials/how-to-use-journalctl-to-view-and-manipulate-systemd-logs
.. _systemd/journal2gelf: https://github.com/systemd/journal2gelf
.. _Sending CoreOS Logs to Loggly: https://www.loggly.com/blog/sending-coreos-logs-to-loggly/
.. _Responsive infrastructure - How to setup rsyslog, elasticsearch and kibana on CoreOS and AWS (2): http://www.itnotes.de/coreos/deployment/tools/infrastructure/aws/docker/fleet/2015/04/03/how-to-setup-rsyslog-elasticsearch-kibana-on-coreos/
.. _Platform logging: http://docs.deis.io/en/latest/managing_deis/platform_logging/
.. _A UDP syslog client in Python — for Windows and UNIX: http://csl.sublevel3.org/post/python-syslog-client/


.. _smallformfactor:

Small form-factor hardware systems
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+ Raspberry Pi
    + `Raspberry Pi Wiki Hub`_
    + `RPi SD cards`_
    + `How to Flash an SD Card for Raspberry Pi`_, by Johnny Winters
        + GitHub `hypriot/flash`_ ("Command line script to flash SD card images for the Raspberry Pi")
    + `Docker Pirates ARMed with explosive stuff`_ (hypriot blog)
        + `Getting started with Docker on your Raspberry Pi`_, hypriot blog, October 13, 2015
        + `Let Docker Swarm all over your Raspberry Pi Cluster`_, by Stefan, July 3, 2015
        + `Heavily ARMed after major upgrade: Raspberry Pi with Docker 1.5.0`_, March 3, 2015
        + `How to use Docker Compose to run complex multi container apps on your Raspberry Pi`_, April 6, 2015
    + Using a Raspberry Pi as a PXE boot server
        + `Raspberry Pi as a PXE, TFTP, NFS, proxy DHCP server`_, by Adam Niedzwiedzki, February 7, 2014
        + `Network booting machines with a PXE server running in a Docker container`_, by Jérôme Petazzoni, December 7, 2013
        + `Raspberry Pi as PXE Server`_, by Cody Bunch, August 19, 2014
        + `How To: Setup a PXE Boot Server on Debian Part 2`_, May 9, 2011
    + `Raspbian Image with Docker 1.5.0 Released for Raspberry Pi Boards`_, by cnxsoft
    + `Docker on Raspberry Pi in 4 Simple Steps`_, by resin.io
    + `Visualize your Raspberry Pi containers with Portainer or UI for Docker`_, by Stefan, October 31, 2016

    + `Cloudy with a chance of Raspberries`_, by Matt Williams
    + `Swarming Raspberry Pi - Part 1`_, by Matt Williams
    + `Let's build a PicoCluster for Docker Swarm`_, Hypriot blog, Mar 23, 2016
        + `5 Node PicoCluster (Raspberry PI)`_, PicoCluster web site
        + `DIY 5 Node Cluster of Raspberry Pi 3s`_, by Nick Smith, April 2016
    + `OpenVPN with 2 factor authentication on the Raspberry Pi`_, by Mark, Coder36 blog, 15 December 2014

+ UP
    + `UP Board`_

+ Beaglebone Black
    + `Using Docker on Beaglebone Black`_, by Mark Fink
    + `Snappy Ubuntu for Devices - The Year of the Linux Countertop!`_


+ CuBox-i
    + `CuBox-i Mini Computer for XBMC/Kodi player, Android TV Box and Linux`_
    + `ArchLinux`_ is one of the available operating systems from `Solid Run <http://www.solid-run.com/support/downloads/>`_

+ Clustering small form-factor devices
    + `#Building ARM cluster Part 1: Collecting , wiring and powering devices`_, by Mateusz Kaczanowski
    + `#Building ARM cluster Part 2: Create and write system image with goback!`_, by Mateusz Kaczanowski
    + `#Building ARM cluster Part 3: Docker, fleet, etcd. Distribute containers!`_, by Mateusz Kaczanowski


Miscellaneous Distributed System Construction
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+ GitHub `uw-dims/ansible-dims-playbooks`_ ("DIMS Ansible playbooks")
+ GitHub `trustedanalytics`_ ("Components for Trusted Analytics Platform")
+ `DebOps`_
+ `The Open Home Lab Stack`_, by Mighty Womble, October 1, 2017
+ `Boot my (secure)->(gov) cloud`_, by Nicki Watt, August 10, 2015

.. _uw-dims/ansible-dims-playbooks: https://github.com/uw-dims/ansible-dims-playbooks/
.. _trustedanalytics: https://github.com/trustedanalytics
.. _DebOps: https://debops.org/
.. _The Open Home Lab Stack: https://hackernoon.com/the-open-home-lab-stack-5e5858722fee
.. _Boot my (secure)->(gov) cloud: https://opencredo.com/boot-my-secure-government-cloud/


Scripting in ``bash``
~~~~~~~~~~~~~~~~~~~~~

+ `Basic grammar rules of Bash`_, BashHackersWiki
+ `Commandlinefu.com`_
    + `Find Duplicate Files (based on size first, then MD5 hash)`_
    + `Recursively remove all empty directories`_
    + GitHub `google/styleguide`_ ("Style guides for Google-originated open-source projects")
        + `Shell Style Guide`_

+ Command line option parsing
    + GitHub `kward/shflags`_ (Automatically exported from https://code.google.com/p/shflags)
    + `Easy Bash Scripting With Shflags`_, by Steve Francia, July 8, 2011
    + `Using getopts in bash shell script to get long and short command line options`_, Stackoverflow post

+ Advanced Bash scripting
    + `How "Exit Traps" Can Make Your Bash Scripts Way More Robust And Reliable`_, by Aaron Maxwell
    + `I set variables in a loop that's in a pipeline. Why do they disappear after the loop terminates? Or, why can't I pipe data to read?`_, BasFAQ/024
    + `The Ultimate Bash Array Tutorial with 15 Examples`_, by Sasikala on June 3, 2010
    + `BashGuide/Arrays`_

+ Debugging Bash scripts
    + `Debug your shell scripts with bashdb`_, by Ben Martin, November 24, 2008
    + `Debugging a script`_, Bash Hackers Wiki
    + `Why does my shell script choke on whitespace or other special characters?`_, StackExchange post by Gilles, May 24 2014


Postfix
~~~~~~~

+ `Postfix Configuration Parameters`_, postfix web site
+ `Postfix Standard Configuration Examples`_, postfix web site
+ `Basic settings in the Postfix main.cf file`_, Rackspace web site, December 29, 2015
+ `Setting up a mail server using Postfix in 5 minutes`_, by Rudd-O
+ `Question about DNSmasq and MX records`_, FreeBSD forums post by danaeckel, March 12, 2013


Dell Edge Server Stuff
~~~~~~~~~~~~~~~~~~~~~~

+ `Problem with PERC H710 Raid Controller`_
+ `Building the LSI 9285-8e Driver for Openfiler 2.99`_, windowsmasher blog
+ `Dell Driver Details: Linux SLES10 SP4 Driver 00.00.05.39-1 for PERC H310 / H710 / H710P / H810 Controllers.`_

.. _Problem with PERC H710 Raid Controller: https://forums.openfiler.com/index.php?/topic/6371-problem-with-perc-h710-raid-controller/
.. _Building the LSI 9285-8e Driver for Openfiler 2.99: http://windowsmasher.wordpress.com/2011/08/13/building-the-lsi-9285-8e-driver-for-openfiler-2-99/
.. _Dell Driver Details\: Linux SLES10 SP4 Driver 00.00.05.39-1 for PERC H310 / H710 / H710P / H810 Controllers.: http://www.dell.com/support/drivers/us/en/555/DriverDetails?driverId=R743M&fileId=3230162503


.. _Journal File Systems: http://www.linuxgazette.com/issue55/florido.html
.. _Linux Headquarters: http://www.linuxhq.com/
.. _CIS 399\: Introduction to System Administration: http://www.cs.uoregon.edu/classes/summer/cis399sysadmin/
.. _UW Mirror of Knoppix distribution: ftp://knoppix.cac.washington.edu/knoppix/
.. _Wacky uses for RAID, /dev/ram, and ramfs: http://www.linuxfocus.org/English/July2001/article210.shtml
.. _rejecting third-party relaying of email: http://staff.washington.edu/dittrich/misc/spam/email.blocking.txt
.. _LinuxPlanet - Tutorials - How to Compile the Linux Kernel: http://www.linuxplanet.com/linuxplanet/tutorials/202/1/
.. _Comparison of several 'tar' implementations vis-a-vis compatibility: http://gd.tuwien.ac.at/utils/archivers/star/README.otherbugs
.. _All tar files are not created equal\: UNIX IN THE ENTERPRISE: http://www.itworld.com/nl/unix_insider/07242003/
.. _GlusterFS: http://www.gluster.org/
.. _Create your own high-performance NAS using GlusterFS: http://www.linuxuser.co.uk/tutorials/create-your-own-high-performance-nas-using-glusterfs
.. _Stop Disabling SELinux!: http://sheltren.com/stop-disabling-selinux
.. _Unix Toolbox: http://cb.vu/unixtoolbox.xhtml
.. _make sendmail reject relaying: http://staff.washington.edu/dittrich/misc/spam/relay.rejection.txt
.. _Linux kernel capabilities FAQ: ftp://ftp.kernel.org/pub/linux/libs/security/linux-privs/kernel-2.2/capfaq-0.2.txt
.. _grsecurity: http://www.grsecurity.net/
.. _Upgrading the Linux Kernel on Red Hat Linux systems: http://www.redhat.com/support/docs/howto/kernel-upgrade/kernel-upgrade.html
.. _System administration (SO 136 A): http://www.iu.hioslo.no/~mark/lectures/sysadm
.. _CIS 410/510, Introduction to System Administration: http://www.cs.uoregon.edu/classes/cis410sysadmin
.. _Raymond: http://raymond.sourceforge.net/
.. _Raspberry Pi Wiki Hub: http://www.elinux.org/RPi_Hub
.. _RPi SD cards: http://www.elinux.org/RPi_SD_cards
.. _How to Flash an SD Card for Raspberry Pi: http://computers.tutsplus.com/articles/how-to-flash-an-sd-card-for-raspberry-pi--mac-53600
.. _hypriot/flash: https://github.com/hypriot/flash
.. _Docker Pirates ARMed with explosive stuff: http://blog.hypriot.com/
.. _Getting started with Docker on your Raspberry Pi: http://blog.hypriot.com/getting-started-with-docker-on-your-arm-device/
.. _Let Docker Swarm all over your Raspberry Pi Cluster: http://blog.hypriot.com/post/let-docker-swarm-all-over-your-raspberry-pi-cluster
.. _Heavily ARMed after major upgrade\: Raspberry Pi with Docker 1.5.0: http://blog.hypriot.com/heavily-armed-after-major-upgrade-raspberry-pi-with-docker-1-dot-5-0
.. _How to use Docker Compose to run complex multi container apps on your Raspberry Pi: http://blog.hypriot.com/post/docker-compose-nodejs-haproxy/
.. _Raspberry Pi as a PXE, TFTP, NFS, proxy DHCP server: http://www.genis-x.com/raspberry-pi-as-a-pxe-tftp-nfs-proxy-dhcp-server.html
.. _Network booting machines with a PXE server running in a Docker container: https://jpetazzo.github.io/2013/12/07/pxe-netboot-docker/
.. _Raspberry Pi as PXE Server: http://blog.codybunch.com/2014/08/19/Raspberry-Pi-as-PXE-Server/
.. _How To\: Setup a PXE Boot Server on Debian Part 2: http://sirlagz.net/2011/05/09/how-to-setup-a-pxe-boot-server-on-debian-part-2/
.. _Raspbian Image with Docker 1.5.0 Released for Raspberry Pi Boards: http://www.cnx-software.com/2015/03/04/raspbian-image-with-docker-1-5-0-released-for-raspberry-pi-boards/
.. _Docker on Raspberry Pi in 4 Simple Steps: https://resin.io/blog/docker-on-raspberry-pi-in-4-simple-steps/
.. _Visualize your Raspberry Pi containers with Portainer or UI for Docker: https://blog.hypriot.com/post/new-docker-ui-portainer/
.. _Cloudy with a chance of Raspberries: http://matthewkwilliams.com/index.php/2015/03/06/cloudy-with-a-chance-of-raspberries/
.. _Swarming Raspberry Pi - Part 1: http://matthewkwilliams.com/index.php/2015/03/21/swarming-raspberry-pi-part-1/
.. _Let's build a PicoCluster for Docker Swarm: http://blog.hypriot.com/post/lets-build-a-pi-docker-picocluster/
.. _5 Node PicoCluster (Raspberry PI): https://preorder.picocluster.com/collections/frontpage/products/5-node-picocluster
.. _DIY 5 Node Cluster of Raspberry Pi 3s: http://climbers.net/sbc/diy-raspberry-pi-3-cluster/
.. _OpenVPN with 2 factor authentication on the Raspberry Pi: http://coder36.blogspot.com/2014/12/raspberry-pi-vpn-with-google.html
.. _UP Board: http://www.up-board.org/
.. _Using Docker on Beaglebone Black: http://www.element14.com/community/people/markfink/blog/2015/02/05/using-docker-on-beaglebone-black
.. _Snappy Ubuntu for Devices - The Year of the Linux Countertop!: http://blog.dustinkirkland.com/2015/01/snappy-ubuntu-for-devices-year-of-linux.html
.. _CuBox-i Mini Computer for XBMC/Kodi player, Android TV Box and Linux: http://www.solid-run.com/products/cubox-i-mini-computer/
.. _#Building ARM cluster Part 1\: Collecting , wiring and powering devices: http://mkaczanowski.com/building-arm-cluster-part-1-collecting-wiring-and-powering-devices/
.. _#Building ARM cluster Part 2\: Create and write system image with goback!: http://mkaczanowski.com/building-arm-cluster-part-2-create-and-write-system-image-with-goback/
.. _#Building ARM cluster Part 3\: Docker, fleet, etcd. Distribute containers!: http://mkaczanowski.com/building-arm-cluster-part-3-docker-fleet-etcd-distribute-containers/
.. _Perl Oasis: http://www.oasis.leo.org/perl/00-oasis.html
.. _Slashdot thread on Automated Support Email Systems: http://ask.slashdot.org/article.pl?sid=04/09/17/228208
.. _IT Tutorials and Interview Questions: http://www.tutorialdownloads.com/
.. _A Perl Tutorial\: Super-Basics: http://virtual.park.uga.edu/humcomp/perl/superbasic.html
.. _Linux Kernel Security (SELinux vs AppArmor vs Grsecurity): http://www.cyberciti.biz/tips/selinux-vs-apparmor-vs-grsecurity.html
.. _Secure Enhanced Linux project: http://www.nsa.gov/selinux/
.. _A curated list of amazingly awesome open source sysadmin resources inspired by Awesome PHP: https://github.com/kahun/awesome-sysadmin


.. _fintanr/weavegs: https://github.com/fintanr/weave-gs
.. _Try on Desktop Button for Docker Hub: https://blog.docker.com/2015/04/introducing-button-on-docker-hub-to-create-containers-locally/
.. _Francisco Augusto (kahun): https://github.com/kahun
.. _Server World: http://www.server-world.info/en/
.. _SunWorld On-Line emagazine: http://www.sun.com/sunworldonline/
.. _Network and System Administration Resources: http://www.iu.hio.no/SystemAdmin/
.. _Back to home page: http://staff.washington.edu/dittrich/
.. _Large File Support in Linux: http://www.suse.de/~aj/linux_lfs.html
.. _Ubuntu: http://www.ubuntulinux.org/
.. _Call Center, Bug Tracking and Project Management Tools for Linux: http://linas.org/linux/pm.html
.. _Troubleshooters.com: http://www.troubleshooters.com/troubleshooters.htm
.. _Useless Use of 'cat' Award: http://www.sektorn.mooo.com/era/unix/award.html
.. _IEEE 1394 (FireWire) for Linux: http://www.linux1394.org/
.. _Kernel-HOWTO: http://www.redhat.com/mirrors/LDP/HOWTO/Kernel-HOWTO.html
.. _Simply exchange files with WOOF: http://www.home.unix-ag.org/simon/woof.html
.. _FAI - Fully Automatic Installation: http://fai-project.org/
.. _Stacki: http://www.stacki.com/
.. _Basic grammar rules of Bash: http://wiki.bash-hackers.org/syntax/basicgrammar
.. _Commandlinefu.com: http://www.commandlinefu.com/
.. _Find Duplicate Files (based on size first, then MD5 hash): http://www.commandlinefu.com/commands/view/3555/find-duplicate-files-based-on-size-first-then-md5-hash
.. _Recursively remove all empty directories: http://www.commandlinefu.com/commands/view/5131/recursively-remove-all-empty-directories
.. _google/styleguide: https://google-styleguide.googlecode.com/
.. _Shell Style Guide: https://google.github.io/styleguide/shell.xml
.. _kward/shflags: https://github.com/kward/shflags
.. _Easy Bash Scripting With Shflags: http://spf13.com/post/easy-bash-scripting-with-shflags
.. _Using getopts in bash shell script to get long and short command line options: http://stackoverflow.com/questions/402377/using-getopts-in-bash-shell-script-to-get-long-and-short-command-line-options/7680682#7680682
.. _How "Exit Traps" Can Make Your Bash Scripts Way More Robust And Reliable: http://redsymbol.net/articles/bash-exit-traps/
.. _I set variables in a loop that's in a pipeline. Why do they disappear after the loop terminates? Or, why can't I pipe data to read?: http://mywiki.wooledge.org/BashFAQ/024
.. _The Ultimate Bash Array Tutorial with 15 Examples: http://www.thegeekstuff.com/2010/06/bash-array-tutorial
.. _BashGuide/Arrays: http://mywiki.wooledge.org/BashGuide/Arrays
.. _Debug your shell scripts with bashdb: https://www.linux.com/news/debug-your-shell-scripts-bashdb
.. _Debugging a script: http://wiki.bash-hackers.org/scripting/debuggingtips
.. _Why does my shell script choke on whitespace or other special characters?: http://unix.stackexchange.com/questions/131766/why-does-my-shell-script-choke-on-whitespace-or-other-special-characters
.. _Postfix Configuration Parameters: http://www.postfix.org/postconf.5.html
.. _Postfix Standard Configuration Examples: http://www.postfix.org/STANDARD_CONFIGURATION_README.html
.. _Basic settings in the Postfix main.cf file: https://support.rackspace.com/how-to/basic-settings-in-the-postfix-maincf-file/
.. _Setting up a mail server using Postfix in 5 minutes: https://rudd-o.com/linux-and-free-software/setting-up-a-mail-server-using-postfix-in-5-minutes
.. _Question about DNSmasq and MX records: https://forums.freebsd.org/threads/38374/
.. _AptGet/Howto: https://help.ubuntu.com/community/AptGet/Howto
.. _How do I create a completely unattended install of Ubuntu?: http://askubuntu.com/questions/122505/how-do-i-create-a-completely-unattended-install-of-ubuntu
.. _Building a Fully Automated Ubuntu Installation Process: http://blog.scottlowe.org/2015/05/20/fully-automated-ubuntu-install/
.. _System Automation – Part 1 – PXE and Preseed: http://www.briancarpio.com/2012/04/04/system-automation-part-1/
.. _25 Useful Basic Commands of APT-GET and APT-CACHE for Package Management: http://www.tecmint.com/useful-basic-commands-of-apt-get-and-apt-cache-for-package-management/

.. _swdevbestpractices:

Software Engineering Best Practices
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+ GitHub `linuxfoundation/cii-best-practices-badge`_ ("Core Infrastructure Initiative Best Practices Badge https://bestpractices.coreinfrastructure.org")
    + `Best Practices Criteria for Free/Libre and Open Source Software (FLOSS) (version 0.5.0)`_
    + `Security`_
    + `Implementation`_
+ `High Cohesion, Loose Coupling`_, the Bojan's Blog, April 8, 2015
+ `Security for developers`_, Mediawiki
    + `Security for developers/Architecture`_, Mediawiki

.. _programminginpython:

Programming in Python
~~~~~~~~~~~~~~~~~~~~~

.. _learningpython:

Learning Python
^^^^^^^^^^^^^^^

+ `Learn Python the Hard Way`_
+ `Python.org`_ (official online documentation and tutorials)
+ Video tutorials
    + GitHub `s16h/py-must-watch`_ ("Must-watch videos about Python: Inspired by js-must-watch. Create pull requests to add more awesome links :-)" )
    + `Transforming Code into Beautiful, Idiomatic Python`_, YouTube video by Raymond Hettinger, March 20, 2013
    + `Python's Class Development Toolkit`_, YouTube video by Raymond Hettinger, March 20, 2013
    + `Raymond Hettinger - Beyond PEP 8 -- Best practices for beautiful intelligible code`_, PyCon 2015
        + Slides can be found at: https://speakerdeck.com/pyconslides/transforming-code-into-beautiful-idiomatic-python-by-raymond-hettinger-1
        + Some of the code can be found here: http://msoucy.me/2015/05/pycon-2015-beyond-pep8/
    + `Raymond Hettinger - Super considered super!`_, PyCon 2015
+ `Dive Into Object-oriented Python`_, by Leonardo Giordani, April 17, 2016
+ `30 Python Language Features and Tricks You May Not Know About`_, by Sahand Saba, May 19, 2014

.. _generalpython:

General Python references
^^^^^^^^^^^^^^^^^^^^^^^^^

+ `Python syntax and semantics`_, Wikipedia
+ `The Hitchhiker's Guide to Python`_
    + `Code Style`
    + `Structuring Your Project`_
+ `Open Sourcing a Python Project the Right Way`_, by Jeff Knupp, August 16, 2013
+ `Cookiecutter: Project Templates Made Easy`_, by Daniel Roy Greenfeld, August 17, 2013
+ `Hacking Secret Cyphers with Python`_
+ `Logilab Python Tools`_
+ `pip`_
+ `Useful Python Functions and Features`_
+ `Code Academy`_ - Learn to code for free
+ `Check IO`_ - Learn Python by playing a game
+ `Anaconda`_ (Completely free enterprise-ready Python distribution for large-scale data processing, predictive analytics, and scientific computing)


.. _advancedpython:

Advanced Python Programming
^^^^^^^^^^^^^^^^^^^^^^^^^^^

+ `How to Create A New Python Module (and deploy it using pip)`_, by liranbh, January 2017
+ `A guide to Python's function decorators`_, by Ayman Farhat, January 2014
+ `Intro to some Python dependencies of OpenStack`_, by Run for the Hills
+ `Easy, clean, reliable Python 2/3 compatibility`_, by Python Charmers Pty Ltd
+ `Easy Signal Handling for Python Daemons`_,  Jeff Hull, August 30, 2012
+ `The Top Mistakes Developers Make When Using Python for Big Data Analytics`_, by Karolina Alexiou
+ `Don’t Slurp: How to Read Files in Python`_, by mssaxm, September 27, 2013 by mssaxm
+ `Python: Multiprocessing large files`_, by Nick, March 29, 2012
+ `Dynaconf - Let your settings to be Dynamic`_, by Bruno Rocha, February 14, 2016
+ `Microservices with Python, RabbitMQ and Nameko`_, by Bruno Rocha, March 4, 2016
    + `nameko`_
+ `How to use findall, finditer, split, sub, and subn in Regular Expressions`_, by mamikon, 2013
+ Pandas
    + `Multi-Processing With Pandas`_, by Gouthaman Balaraman, November 19, 2014
    + `Pandas: Data Analysis with Python`_, by Carsten Schnober
    + `Exploring U.S. Traffic Fatality Data`_ (using Python and Pandas), by Ben Van Dyke, December 16, 2015

+ `Adventures in Optimizing Text Processing`_ (Lessons learned while post-processing 1.75 billion lines of Hadoop output), by Michael Richman, January 21, 2014
+ `Git revision numbers for setuptools packages`_, by Christopher Berner, February 26, 2012
+ `A template for Python packages, including a sound setup.py and Makefile for tagging releases`_ by hcarvalhoalves
+ `How To Quickly Compute The Mandelbrot Set In Python`_, by Jean Francois Puget, December 28, 2015
+ `A Globals Class pattern for Python`_, by Steve Ferg, October 20, 2010
+ GitHub `Yelp/undebt`_ ("A fast, straightforward, reliable tool for performing massive, automated code refactoring")
+ `Create, use, and remove temporary files securely`_, Openstack web site

.. _pythonclis:

Command line programs in Python
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+ `Writing Awesome Command-Line Programs in Python`_, YouTube video from EuroPython 2014, July 24, 2014
+ GitHub `openstack/cliff`_ ("Command Line Interface Formulation Framework http://openstack.org")
+ `[openstack-dev] [oslo][openstackclient] transferring maintenance of cliff to the OpenStack client team`_, by Doug Hellmann, February 26, 2015
    + `Oslo`_ (OpenStack Common Libraries)
        + GitHub OpenStack `Oslo repos`_
    + `cmd2`_
    + `Python Apps the Right Way: entry points and scripts`_, by Chris Warrick, September 15, 2014
+ `worked examples of argparse and python logging`_, Gist by olooney
+ `Accessing value from either os.environ or argparse`_, Stackexchange post


Python IDEs, shells, and debuggers
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

+ PyCharm
    + `PyCharm Overview`_, YouTube video by JetBrains, May 5, 2014
    + `9 Reasons You Should be Using PyCharm`_, by Michael Kennedy, November 19, 2015
    + `How to Get Started with PyCharm and Have a Productive Python IDE`_, by Pedro Kroger
    + `Productive Python with PyCharm`_, by Paul Everitt, 2015
    + `Install PyCharm on Ubuntu Linux`_, by Akbar S. Ahmed, February 10, 2015
    + `Debug Support in Interactive Python Console`_, YouTube video by JetBrains, May 16, 2014
    + `Configure PyCharm to use virtualenv`_, by Akbar S. Ahmed, February 10, 2015
    + `An Epic Review of PyCharm 3 from a Vim User’s Perspective`_, by Andrew Brookins
    + `How do not waste time in PyCharm`_, YouTube vide by Paqmind, October 18, 2014

+ `IPython`_
+ `full: April 2014 Meetup - Matt Boehm and Python debuggers`_, DCPython tutorial session

.. _virtualenvs:

Python virtual environments
^^^^^^^^^^^^^^^^^^^^^^^^^^^

    + `virtualenv`_ source code
    + `Virtual Environments`_, Python Guide docs
    + `Python Power Tools: virtualenv`_ video by Tuts+ Code
    + `Python Power Tools: virtualenvwrapper`_ video by Tuts+ Code
    + `Python: pyenv, pyvenv, virtualenv – What’s the Difference?`_, by Abu Ashraf Masnun, April 10, 2016
    + `Reverse-engineering Ian Bicking's brain: inside pip and virtualenv`_, presented by Carl Meyer at PyCon 2011, Atlanta
        + `Slides of Carl Meyer's presentation`_

    + `Configure PyCharm to use virtualenv`_, by Akbar S. Ahmed, February 10, 2015
    + `Development Environment in Python - Part 1: Virtualenv and Pip`_, by Michael Herman
    + `Development Environment in Python - Part 2: Git and Github`_, by Michael Herman
    + `Running IPython cleanly inside a virtualenv`_
    + `Automatically load a virtualenv when running a script`_, stackoverflow, May 15, 2014
    + `Virtualenv's bin/activate is Doing It Wrong`_, datagrok / gist:2199506, July 3, 2014
    + `Virtualenv the Docker way`_, by Justyna Ilczuk, Nov 16, 2014


.. _testautomation:

Testing and Test Automation
~~~~~~~~~~~~~~~~~~~~~~~~~~~

+ `Ned Batchelder: Getting Started Testing - PyCon 2014`_, PyCon 2014
+ `Robot Framework`_
    + `How To Configure PyCharm for Robot Framework`_, YouTube video by KWoodScreencast, July 2014
    + `Robot Framework Tutorial 2- First Script`_

+ GitHub `sstephenson/bats`_ ("Bats: Bash Automated Testing System")
    + `Testing Bash scripts with Bats`_, by Spike Grobstein, September 7, 2013
    + `How to use Bats to test your command line tools`_, engineyard, April 29, 2014
    + GitHub `duggan/pontoon/test/bats`_
    + GitHub `jenkinsci/docker/tests`_
    + More `Projects using Bats`_

.. _Ned Batchelder\: Getting Started Testing - PyCon 2014: https://youtu.be/FxSsnHeWQBY
.. _Robot Framework: http://robotframework.org/
.. _How To Configure PyCharm for Robot Framework: https://youtu.be/r3Mg60r1Jjk
.. _Robot Framework Tutorial 2- First Script: https://www.youtube.com/watch?v=LhUre0hu8I8
.. _sstephenson/bats: https://github.com/sstephenson/bats#bats-bash-automated-testing-system
.. _Testing Bash scripts with Bats: http://blog.spike.cx/post/60548255435/testing-bash-scripts-with-bats
.. _How to use Bats to test your command line tools: https://blog.engineyard.com/2014/bats-test-command-line-tools
.. _duggan/pontoon/test/bats: https://github.com/duggan/pontoon/tree/master/test/bats
.. _jenkinsci/docker/tests: https://github.com/jenkinsci/docker/tree/master/tests
.. _Projects using Bats: https://github.com/sstephenson/bats/wiki/Projects-Using-Bats


.. _sphinxrest:

Sphinx + reST
~~~~~~~~~~~~~

+ `Sphinx`_
    + `Sphinx Style Guide`_
    + `Sphinx Tutorial v0.1`_ talk by Brandon Rhodes from PyCon 2013
    + `Documenting Your Project Using Sphinx`_
    + `Easy and beautiful documentation with Sphinx`_

+ `Restructured Text (reST) and Sphinx CheatSheet`_
    + `The reStructuredText_ Cheat Sheet: Syntax Reminders`_
    + `Tables`_
+ `reStructuredText tool support`_
+ `Quick reStructuredText`_
+ `ReadTheDocs`_
+ `Don't be afraid to commit`_
+ `Sphinx Autodoc Tutorial for Dummies`_
+ `How to generate sphinx documentation for python code running in an embedded system`_
+ `Problems with StructuredText`_
+ `Automatically Generating Documentation for All Python Package Contents`_, stackoverflow.com
+ `sphinx.ext.intersphinx – Link to other projects’ documentation`_
    + GitHug Gist `shimizukawa/conf.py`_ (Sphinx: Link to outer non-sphinx document by using intersphinx. https://groups.google.com/d/topic/sphinx-users/P_FolrZVoNg/discussion)

+ `Python Continuous Documentation`_
+ `sphinxcontrib-bibtex`_
+ `sphinx-contrib`_ at Bitbucket
+ StackOverflow thread: `Using Sphinx to write personal websites and blogs`_
+ `ABlog for Sphinx`_
+ `sphinx.ext.graphviz – Add Graphviz graphs`_
    + `Google search for 'graphviz dot tutorial'`_

.. _usinggit:

Git
~~~

+ `Git`_
+ `Git tips from the trenches`_, February 1, 2014
+ `Learn Git Branching`_ (really cool animated tutorial, visualizing Git concepts)
+ `Git Interactive Rebase, Squash, Amend and Other Ways of Rewriting History`_, by Tute Costa, November 3, 2014
+ `Git: Using topic branches and interactive rebasing effectively`_, by kumar303
+ `Git - When to Merge vs. When to Rebase`_, by Derek Gourlay, February 15, 2016

+ Viewing Git history
    + `2.3 Git Basics - Viewing the Commit History`_, the Git Book
    + `gitk`_
    + GitHub `esc/git-big-picture`_
    + `Visualizing branch topology in git`_, Stackoverflow post by Benjol, December 3, 2009

+ Git merging and conflict resolution
    + `kdiff3`_
    + `meld`_
        + `Git merging using Meld`_, Stackoverflow thread, June 21, 2012
        + `Three way git merging with meld`_, by Lukáš Zapletal, September 17, 2012
        + `Painless Merge Conflict Resolution in Git`_, by Kevin Wu Won, September 14, 2010

+ Oops. I didn't mean to do that... (Ugh!)
    + `How to undo (almost) anything with Git`_, GitHub blog post by jaw6, June 8, 2015
    + `Undo Almost Anything with Git webinar`_, YouTube video by Peter Bell and Michael Smith, February 11, 2014
    + `Undoing Changes`_, Git tutorial, attlasian.com

+ `GitHub`_ for hosting your Git repositories
   + `Fork A Repo`_ (GitHub Help)
   + `Forking Projects`_, (GitHub Guides)
   + `Syncing a fork`_ (GitHub Help)
   + `Pushing to a remote`_ (GitHub Help)

+ `git-flow`_ utilities to follow the `Vincent Dreisen branching workflow`_
   + `Getting Started – Git-Flow`_, yakiloo

   .. image:: images/git-flow-overview.jpg
      :width: 60 %
      :alt: Git-Flow Work Flow Overview
      :align: center
      :target: https://jacovanstaden.files.wordpress.com/2011/03/git-flow-overview.jpg

+ `hub`_ (Git front end for GitHub)
+ `HubFlow`_ (GitFlow for GitHub)
   + `Using GitFlow with GitHub`_ (Note: At this time, this workflow is designed for developers who belong to the same GitHub organisation. Although you are welcome to use it for opensource projects, it is designed for companies like DataSift who are using private repos on GitHub.)
   + `Versioning`_
   + `GitHub Flow Like a Pro with these 13 Git Aliases`_
   + `Development flow with git flow, github`_, by Vysakh Sreenivasan
   + `GitFlow: safely merge develop changes to a feature branch`_, stackoverflow thread

+ `Comparing Workflows`_, Atlassian Tutorials
+ `bumpversion`_ (can flexibly increment version numbers and commit/tag in Git)
   + `bumpversion screencast`_ showing bumpversion in action
   + `A Python Versioning Workflow With Bumpversion`_
   + `PEP 440 -- Version Identification and Dependency Specification`_ (Python versioning specification that addresses several limitations of the previous attempt at a standardized approach to versioning, as described in PEP 345 and PEP 386.)

+ Git aliases and advanced tricks
   + `Includes in your git config`_, by Aurélien's room, December 5, 2015
   + `Using git's include for private configuration information (like github tokens)`_
   + `Protect Your Private Data Using Gitconfig Include Directive`_, Basetta.Bz, January 28, 2013
   + `One weird trick for powerful Git aliases`_, by Nicola Paolucci, October 3, 2014
   + GitHubGist `mwhite/git-aliases.md`_ (The Ultimate Git Alias Setup)
   + `Must Have Git Aliases: Advanced Examples`_, by @durdn
   + GitHubGist `mcxiaoke/.gitconfig`_
   + `What are your favorite Git aliases?`_, Reddit ``r/git`` post,
   + `SCM Breeze`_ (GitHub Gist `ndbroadbent/scm_breeze` ("Adds numbered shortcuts to the output git status, and much more http://madebynathan.com/2011/10/18/git-shortcuts-like-youve-never-seen-before/"))
   + Encrypting some/all of a Git repository
       + `encrypted repositories?`_, Gmane thread
       + GitHub `AGWA/git-crypt`_ ("Transparent file encryption in git https://www.agwa.name/projects/git-crypt/")
       + GitHub Gist `shadowhand/encrypted-git-repo.md`_ ("Transparent Git Encryption")
   + `7.14 Git Tools - Credential Storage`_, Git book

+ Mac OS X and Windows issues with Git
   + `Git on Mac OS X: Don't ignore case!`_, by Howard Lewis Ship, July 28, 2010
   + `How do I commit case-sensitive only filename changes in Git?`_, Stackoverflow, July 16, 2013
   + `Case sensitivity in Git`_, Stackoverflow, January 18, 2012 (has solution for Mac OS X users)

+ `version.py`_ Python script for getting version number from Git to use in ``setup.py``

+ Advanced tasks (DANGER)
   + `How to delete files permanently from your local and remote git repositories`_, by Anoopjohn, February 20, 2014
   + GitHub `aaronzirbes/shrink-git-repo.sh`_ ("This script will help you remove large files from your git repo history and shrink the size of your repository.")
   + `How to Shrink a Git Repository`_, by Steve Lorek, May 11, 2012


Agile/Scrum
~~~~~~~~~~~

+ `Agile methodology`_
+ `Scrum methodology`_
+ `Learn Scrum in 7 Minutes!`_, by techexcel, (YouTube video)
+ `Scrum and Kanban`_, Kanbantool,
+ `Introduction to Scrum - CollabNet Scrum Training Part 1`_, YouTube
+ `Jira Agile`_
+ Humor about Agile/Scrum
    + `I Need Agile Methodology`_, YouTube [Play on the hilarious `iPhone vs. Evo`_ video. "NSFW because of language (though that's probably relative to your work environment)."]
    + `Another perspective on SCRUM`_, YouTube

Continuous Integration and DevOps
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+ `Continuous Integration`_
+ `Jenkins CI`_
     + `Pipeline as Code with Jenkins`_, Jenkins web sit
     + `GitHub Organization Folder Plugin`_, Jenkins Plugin web site
     + `Pipeline Stage View Plugin`_, Jenkins Plugin web site
     + `JENKINS_HOME directory`_
     + `Distributed builds`_
     + `Automatically Generating Jenkins Jobs`_, by Jim Graf, March 11, 2016
     + `Simple Continuous Integration / Deployment With Jenkins`_, by Randall Degges
     + `7 Habits of Highly Effective Jenkins Users`_, by Andrew Beyer, July 28, 2011
     + `A Back Up And Restore Recipe for Jenkins Metadata`_, by chris, March 16, 2015
     + `How To Deploy Jenkins Completely Pre-Configured - Automating Jenkins`_, by Emmet O'Grady, October 11, 2016
     + `Jenkins2 Pipeline jobs using Groovy code in Jenkinsfile`_, by Wilson Mar, August 3, 2016
     + `Creating Jenkins pipelines with Ansible, part 1`_, by Joel Wilsson, Augusst 6, 2016
     + `Creating Jenkins pipelines with Ansible, part 2`_, by Joel Wilsson, August 10, 2016

+ `GoCD`_ ("Simplify Continuous Delivery")

+ `What is DevOps?`_
+ `Implementing Continuous Delivery: Jenkins or Bamboo?`_, by Francis Adanza, April 12, 2016

Kanban method
~~~~~~~~~~~~~

+ `Kanban (Development)`_, Wikipedia
+ `Kanban Applied to Software Development: from Agile to Lean`_, by Kenji Hiranabe, January 14, 2008
+ `Kanban vs. Scrum: Kanban is NOT for Software Development, but Scrum is!`_, by charlesbradley, February 4, 2013
+ `How To Get Started With Kanban In Software Development`_, by Derick Bailey, August 5, 2009
+ `Adventures in Lean`_, by Derick Bailey, November 19, 2008

Software Engineering Project Management
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+ `44 engineering management lessons`_, by Slava Akhmechet, October 3, 2014

Messaging using AMQP
~~~~~~~~~~~~~~~~~~~~

+ `AMQP and Beyond: Messaging by Extending RabbitMQ`_, by Tony Garnock-Jones
+ `kombu - AMQP Messaging Framework for Python`_, Version: 1.0.5
+ `Postage - a RabbitMQ-based Component Python Library`_
+ `Federated Queues`_, RabbitMQ web site
+ `Distributed RabbitMQ brokers`_, RabbitMQ web site
+ `Alvaro Videla - Building a Distributed Data Ingestion System with RabbitMQ`_, YouTube, Jul 16, 2014
+ `Distributed log aggregation with RabbitMQ Federation`_, by Alvaro Videla, December 17, 2013
+ `Routing Topologies for Performance and Scalability with RabbitMQ`_, by Helena Edelson, April 1, 2011
+ `Configuring SSL for RabbitMQ`_, by Richard, January 27, 2013
+ `Securing the RabbitMQ Management Console with SSL`_, by Richard, January 27, 2013


.. _opensource:

Software licensing and Open Source
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

+ `tl;dr Legal`_ quick references

    + `Apache 2.0 License`_
    + `BSD 3-Clause License (Revised)`_
    + `Apache 2.0 and BSD 3-Clause Licenses (Merged)`_

+ `How to Make Money from Open Source`_, by pieterh, September 18, 2012
+ `How To Capture an Open Source Project`_, by pieterh, October 21, 2013
+ `OSI Hopes To Decrease Number of Licenses`_, Slashdot (Bruce Parens, creator of the Open Source definition, hopes to get back to just three Open Source licenses from which to chose, rather than over 30)
+ `Understanding Open Source Software`_, by Red Hat's Mark Webbink, Esq., GROKLAW
+ `BSD and GPL Licensing`_, wikipedia
+ `The Open Source Initiative`_ has a `list of open source licenses`_
+ `Open Source Licensing: Links and Resources`_, wasabisystems.com
+ `GPL v3 drafting process`_ (Current Release: January 16, 2006: Next Release: Anticipated May or June 2006)
+ `MySQL's "dual-license" model`_
+ `Trademark and OSS`_, Software Pluralism, University of Washington Law School
+ `Derivative Works`_, Software Pluralism, University of Washington Law School
+ `Patent Risks`_, Software Pluralism, University of Washington Law School
+ Dual-licensing model

    + `Dual Licensing in Open Source Software Industry`_, by Mikko Välimä, January, 2003
    + `Dual Licensing: Having Your Cake and Eating It Too`_, by Philip H.  Albert, LinuxInsider, November 16, 2004
    + `Dual Licensing`_, OSS Watch
    + `MySL AB FLOSS Exception`_

+ Open Source licenses in the courts

    + `Litigation in Open Source`_, by Jason B. Wacha, Vice President of Corporate Affairs and General Counsel, MontaVista Software, Inc., August 8, 2004
    + `Linksys routers caught up in open source dispute`_
    + `Is Linksys shirking the GPL? (Maybe not.)`_, O'Reilly OnLAMP.com
    + `Linux's Hit Men`_, by Daniel Lyons, Forbes.com, October 14, 2003 [Discusses the problems of Cisco Systems' purchase of Linksys (manufacturer of home routers), which had GPL'd code on the Broadcom chips it used.]
    + `GPL: IT'S THE LAW`_, by Nancy Cohen

Miscellaneous
~~~~~~~~~~~~~

+ MIL-STD-498

    + `A forgotten military standard that saves weeks of work (by providing free project management templates)`_, by Kristof Kovacs
    + `MIL-STD-498 Software Development and Documentation (all pdf files)`_
    + http://search.cpan.org/~softdia/Docs-US_DOD-STD2167A/

+ `How HipChat Stores And Indexes Billions Of Messages Using ElasticSearch And Redis`_
+ `Kuyruk 0.20.3`_
+ `Celery: Distributed Task Queue`_
+ `Kronuz / celery`_
+ `Tuple Space`_
+ `Useful one-line scripts for sed`_,


.. _linuxfoundation/cii-best-practices-badge: https://github.com/linuxfoundation/cii-best-practices-badge
.. _Best Practices Criteria for Free/Libre and Open Source Software (FLOSS) (version 0.5.0): https://github.com/linuxfoundation/cii-best-practices-badge/blob/master/doc/criteria.md
.. _Security: https://github.com/linuxfoundation/cii-best-practices-badge/blob/master/doc/security.md
.. _Implementation: https://github.com/linuxfoundation/cii-best-practices-badge/blob/master/doc/implementation.md
.. _High Cohesion, Loose Coupling: https://thebojan.ninja/2015/04/08/high-cohesion-loose-coupling/
.. _Security for developers: https://www.mediawiki.org/wiki/Security_for_developers
.. _Security for developers/Architecture: https://www.mediawiki.org/wiki/Security_for_developers/Architecture
.. _Learn Python the Hard Way: http://learnpythonthehardway.org/book/index.html
.. _Python.org: https://www.python.org/
.. _s16h/py-must-watch: https://github.com/s16h/py-must-watch/blob/master/README.md
.. _Transforming Code into Beautiful, Idiomatic Python: https://youtu.be/OSGv2VnC0go
.. _Python's Class Development Toolkit: https://youtu.be/HTLu2DFOdTg
.. _Raymond Hettinger - Beyond PEP 8 -- Best practices for beautiful intelligible code: https://youtu.be/wf-BqAjZb8M
.. _Raymond Hettinger - Super considered super!: https://youtu.be/EiOglTERPEo
.. _Dive Into Object-oriented Python: https://speakerdeck.com/lgiordani/dive-into-object-oriented-python
.. _30 Python Language Features and Tricks You May Not Know About: http://sahandsaba.com/thirty-python-language-features-and-tricks-you-may-not-know.html
.. _Python syntax and semantics: https://en.wikipedia.org/wiki/Python_syntax_and_semantics
.. _Code Style: http://docs.python-guide.org/en/latest/writing/style/
.. _The Hitchhiker's Guide to Python: http://docs.python-guide.org/en/latest
.. _Structuring Your Project: http://docs.python-guide.org/en/latest/writing/structure/
.. _Open Sourcing a Python Project the Right Way: https://www.jeffknupp.com/blog/2013/08/16/open-sourcing-a-python-project-the-right-way/
.. _Cookiecutter\: Project Templates Made Easy: http://www.pydanny.com/cookie-project-templates-made-easy.html
.. _Hacking Secret Cyphers with Python: http://inventwithpython.com/blog/2013/04/15/hacking-secret-ciphers-with-python-released/
.. _Logilab Python Tools: https://www.logilab.org/view?rql=Project%20P%20ORDERBY%20N%20WHERE%20P%20name%20N&vtitle=all%20projects
.. _pip: https://pip.pypa.io/en/latest/index.html
.. _Useful Python Functions and Features: http://pypix.com/tools-and-tips/python-functions/
.. _Easy, clean, reliable Python 2/3 compatibility: http://python-future.org/quickstart.html
.. _Writing Awesome Command-Line Programs in Python: https://youtu.be/gR73nLbbgqY
.. _openstack/cliff: https://github.com/openstack/cliff
.. _[openstack-dev] [oslo][openstackclient] transferring maintenance of cliff to the OpenStack client team: https://openstack.nimeyo.com/34635/openstack-openstackclient-transferring-maintenance-openstack
.. _Oslo: https://wiki.openstack.org/wiki/Oslo
.. _Oslo repos: https://github.com/openstack?utf8=%E2%9C%93&query=oslo
.. _cmd2: https://pypi.python.org/pypi/cmd2
.. _Python Apps the Right Way\: entry points and scripts: https://chriswarrick.com/blog/2014/09/15/python-apps-the-right-way-entry_points-and-scripts/
.. _worked examples of argparse and python logging: https://gist.github.com/olooney/8155400
.. _Accessing value from either os.environ or argparse: http://codereview.stackexchange.com/questions/88656/accessing-value-from-either-os-environ-or-argparse
.. _PyCharm Overview: https://youtu.be/iutkLjeGc6w?list=PLQ176FUIyIUY5Ii58pzoZhS_3qIBL80nz
.. _9 Reasons You Should be Using PyCharm: https://blog.michaelckennedy.net/2015/11/19/9-reasons-you-should-be-using-pycharm/
.. _How to Get Started with PyCharm and Have a Productive Python IDE: http://pedrokroger.net/getting-started-pycharm-python-ide/
.. _Productive Python with PyCharm: http://www.pauleveritt.org/productive/
.. _Install PyCharm on Ubuntu Linux: http://exponential.io/blog/2015/02/10/install-pycharm-on-ubuntu-linux/
.. _Debug Support in Interactive Python Console: https://youtu.be/JcOCNgXXhmE?list=PLQ176FUIyIUY5Ii58pzoZhS_3qIBL80nz
.. _An Epic Review of PyCharm 3 from a Vim User’s Perspective: http://andrewbrookins.com/tech/one-year-later-an-epic-review-of-pycharm-2-7-from-a-vim-users-perspective/
.. _How do not waste time in PyCharm: https://youtu.be/uViQV2NncIw
.. _IPython: http://ipython.org/
.. _full\: April 2014 Meetup - Matt Boehm and Python debuggers: http://youtu.be/tLMuxAuVbgI
.. _virtualenv: https://virtualenv.pypa.io/en/latest/
.. _Virtual Environments: http://docs.python-guide.org/en/latest/dev/virtualenvs/
.. _Python Power Tools\: virtualenv: https://www.youtube.com/watch?v=IX-v6yvGYFg
.. _Python Power Tools\: virtualenvwrapper: https://www.youtube.com/watch?v=UcbUXq0wd-8
.. _Python\: pyenv, pyvenv, virtualenv – What’s the Difference?: http://masnun.com/2016/04/10/python-pyenv-pyvenv-virtualenv-whats-the-difference.html
.. _Python\: pyenv, pyvenv, virtualenv – What’s the Difference?: http://masnun.com/2016/04/10/python-pyenv-pyvenv-virtualenv-whats-the-difference.html
.. _Reverse-engineering Ian Bicking's brain\: inside pip and virtualenv: http://pyvideo.org/video/389/pycon-2011--reverse-engineering-ian-bicking--39-s
.. _Slides of Carl Meyer's presentation: http://carljm.github.io/pipvirtualenv-preso/#1
.. _Configure PyCharm to use virtualenv: http://exponential.io/blog/2015/02/10/configure-pycharm-to-use-virtualenv/
.. _Development Environment in Python - Part 1\: Virtualenv and Pip: http://youtu.be/yOeUKxVNQZU
.. _Development Environment in Python - Part 2\: Git and Github: http://youtu.be/9xePqfHP7k8
.. _Running IPython cleanly inside a virtualenv: https://coderwall.com/p/xdox9a/running-ipython-cleanly-inside-a-virtualenv
.. _Automatically load a virtualenv when running a script: http://stackoverflow.com/questions/23678993/automatically-load-a-virtualenv-when-running-a-script
.. _Virtualenv's bin/activate is Doing It Wrong: https://gist.github.com/datagrok/2199506
.. _Virtualenv the Docker way: http://tinystruggles.com/2014/11/16/docker-virtualenv.html
.. _Comparing 7 Python data visualization tools: https://www.dataquest.io/blog/python-data-visualization-libraries/
.. _Croizat: http://croizat.sourceforge.net/
.. _readability: https://github.com/gfxmonk/python-readability/
.. _pipe2py: https://github.com/ggaughan/pipe2py
.. _Bokeh: http://bokeh.pydata.org/en/latest/
.. _Dark Web OSINT With Python Part Three\: Visualization: https://www.bellingcat.com/guides-en/2016/09/01/dark-web-osint-python-part-three-visualization/
.. _Code Academy: http://www.codecademy.com/
.. _Check IO: http://www.checkio.org/
.. _Anaconda: https://store.continuum.io/cshop/anaconda/
.. _A guide to Python's function decorators: http://thecodeship.com/patterns/guide-to-python-function-decorators/
.. _How to Create A New Python Module (and deploy it using pip): https://www.reddit.com/r/Python/comments/5gl1lx/how_to_create_a_new_python_module_and_deploy_it/
.. _Intro to some Python dependencies of OpenStack: https://blog-slagle.rhcloud.com/?p=124
.. _Easy Signal Handling for Python Daemons: http://engineerwithoutacause.com/easy-signal-handling-for-python-daemons.html
.. _The Top Mistakes Developers Make When Using Python for Big Data Analytics: https://www.airpair.com/python/posts/top-mistakes-python-big-data-analytics
.. _Don’t Slurp\: How to Read Files in Python: http://axialcorps.com/2013/09/27/dont-slurp-how-to-read-files-in-python/
.. _Python\: Multiprocessing large files: http://www.ngcrawford.com/2012/03/29/python-multiprocessing-large-files/
.. _Dynaconf - Let your settings to be Dynamic: http://brunorocha.org/python/dynaconf-let-your-settings-to-be-dynamic.html
.. _How to use findall, finditer, split, sub, and subn in Regular Expressions: http://code.runnable.com/UqV9JYh03AFGAACS/how-to-use-findall-finditer-split-sub-and-subn-in-regular-expressions-in-python-for-regex
.. _Microservices with Python, RabbitMQ and Nameko: http://brunorocha.org/python/microservices-with-python-rabbitmq-and-nameko.html
.. _nameko: https://nameko.readthedocs.org/en/stable/key_concepts.html
.. _Multi-Processing With Pandas: http://gouthamanbalaraman.com/blog/distributed-processing-pandas.html
.. _Pandas\: Data Analysis with Python: http://www.admin-magazine.com/HPC/Articles/Data-Analysis-with-Panda
.. _Exploring U.S. Traffic Fatality Data: http://blog.yhathq.com/posts/traffic-fatalities-in-us.html
.. _Adventures in Optimizing Text Processing: http://word.bitly.com/post/74069870671/optimizing-text-processing
.. _Git revision numbers for setuptools packages: http://cberner.com/2012/02/26/git-revision-numbers-for-setuptools-packages/
.. _A template for Python packages, including a sound setup.py and Makefile for tagging releases: https://github.com/hcarvalhoalves/python-package-template
.. _How To Quickly Compute The Mandelbrot Set In Python: https://www.ibm.com/developerworks/community/blogs/jfp/entry/How_To_Compute_Mandelbrodt_Set_Quickly?lang=en
.. _A Globals Class pattern for Python: https://pythonconquerstheuniverse.wordpress.com/2010/10/20/a-globals-class-pattern-for-python/
.. _Yelp/undebt: https://github.com/Yelp/undebt
.. _Create, use, and remove temporary files securely: https://security.openstack.org/guidelines/dg_using-temporary-files-securely.html
.. _A fast, straightforward, reliable tool for performing massive, automated code refactoring: https://github.com/Yelp/undebt
.. _Sphinx: http://sphinx-doc.org
.. _Sphinx Style Guide: http://documentation-style-guide-sphinx.readthedocs.org/en/latest/style-guide.html
.. _Documenting Your Project Using Sphinx: https://pythonhosted.org/an_example_pypi_project/sphinx.html
.. _Easy and beautiful documentation with Sphinx: http://www.ibm.com/developerworks/library/os-sphinx-documentation/
.. _Restructured Text (reST) and Sphinx CheatSheet: http://thomas-cokelaer.info/tutorials/sphinx/rest_syntax.html
.. _Tables: http://thomas-cokelaer.info/tutorials/sphinx/rest_syntax.html#tables
.. _The reStructuredText_ Cheat Sheet\: Syntax Reminders: http://docutils.sourceforge.net/docs/user/rst/cheatsheet.txt
.. _reStructuredText tool support: http://stackoverflow.com/questions/2746692/restructuredtext-tool-support
.. _Quick reStructuredText: http://docutils.sourceforge.net/docs/user/rst/quickref.html
.. _ReadTheDocs: https://readthedocs.org/
.. _Don't be afraid to commit: http://dont-be-afraid-to-commit.readthedocs.io/en/latest/
.. _Sphinx Autodoc Tutorial for Dummies: https://codeandchaos.wordpress.com/2012/07/30/sphinx-autodoc-tutorial-for-dummies/
.. _How to generate sphinx documentation for python code running in an embedded system: https://developer.ridgerun.com/wiki/index.php/How_to_generate_sphinx_documentation_for_python_code_running_in_an_embedded_system
.. _Problems with StructuredText: http://docutils.sourceforge.net/docs/dev/rst/problems.html
.. _Automatically Generating Documentation for All Python Package Contents: http://stackoverflow.com/questions/4616693/automatically-generating-documentation-for-all-python-package-contents
.. _Sphinx Tutorial v0.1: http://brandons-sphinx-tutorial.readthedocs.org/en/v0.1/
.. _sphinx.ext.intersphinx – Link to other projects’ documentation: http://sphinx-doc.org/latest/ext/intersphinx.html#confval-intersphinx_mapping
.. _shimizukawa/conf.py: https://gist.github.com/shimizukawa/3978232
.. _Python Continuous Documentation: https://developer.rackspace.com/blog/python-continuous-documentation/
.. _sphinxcontrib-bibtex: http://sphinxcontrib-bibtex.readthedocs.org/en/latest/index.html
.. _Using Sphinx to write personal websites and blogs: http://stackoverflow.com/questions/1576340/using-sphinx-to-write-personal-websites-and-blogs
.. _sphinx-contrib: https://bitbucket.org/birkenfeld/sphinx-contrib/
.. _ABlog for Sphinx: http://ablog.readthedocs.org/
.. _sphinx.ext.graphviz – Add Graphviz graphs: http://sphinx-doc.org/ext/graphviz.html

.. _Python Data Mining Resources: http://www.lleess.com/2013/03/python-data-mining-resources.html
.. _Natural Language Toolkit (NLTK) 2.0: http://nltk.org/
.. _Scrapy: http://scrapy.org/

.. _Dive into Machine Learning: http://hangtwenty.github.io/dive-into-machine-learning
.. _hangtwenty/dive-into-machine-learning: https://github.com/hangtwenty/dive-into-machine-learning
.. _The Three Generations of Big Data Processing: http://www.slideshare.net/Datadopter/the-three-generations-of-big-data-processing
.. _DataCatalogs.org: http://datacatalogs.org/
.. _Handy Python Libraries for Formatting and Cleaning Data: https://blog.modeanalytics.com/python-data-cleaning-libraries/
.. _Machine Learning in Python Has Never Been Easier!: http://blog.bigml.com/2012/05/04/machine-learning-in-python-has-never-been-easier/
.. _scikit-learn\: machine learning in Python: http://scikit-learn.org/stable/
.. _Overview of clustering methods: http://scikit-learn.org/stable/modules/clustering.html
.. _Self Organizing Maps in Python: http://paraschopra.com/sourcecode/SOM/index.php
.. _OpenCV-Python Tutorials\: Machine Learning: http://opencv-python-tutroals.readthedocs.org/en/latest/py_tutorials/py_ml/py_table_of_contents_ml/py_table_of_contents_ml.html
.. _Predicting Airbnb Listing Prices with Scikit-Learn and Apache Spark: https://www.mapr.com/blog/predicting-airbnb-listing-prices-scikit-learn-and-apache-spark#.VxlPkdN5juk.twitter
.. _Another perspective on SCRUM: http://www.youtube.com/watch?v=Sygm9x9sBEo
.. _Scrum and Kanban: http://kanbantool.com/kanban-library/scrum-and-kanban
.. _Back to home page: http://staff.washington.edu/dittrich/
.. _Kuyruk 0.20.3: https://pypi.python.org/pypi/Kuyruk/0.20.3
.. _Tuple Space: http://en.wikipedia.org/wiki/Tuple_space
.. _How HipChat Stores And Indexes Billions Of Messages Using ElasticSearch And Redis: http://highscalability.com/blog/2014/1/6/how-hipchat-stores-and-indexes-billions-of-messages-using-el.html
.. _Kanban Applied to Software Development\: from Agile to Lean: http://www.infoq.com/articles/hiranabe-lean-agile-kanban
.. _Inferring templates from a collection of strings: http://stackoverflow.com/questions/6261714/inferring-templates-from-a-collection-of-strings
.. _Kanban (Development): http://en.wikipedia.org/wiki/Kanban_(development)
.. _A forgotten military standard that saves weeks of work (by providing free project management templates): http://kkovacs.eu/free-project-management-template-mil-std-498
.. _MIL-STD-498 Software Development and Documentation (all pdf files): http://www.letu.edu/people/jaytevis/Software-Engineering/MIL-STD-498/MIL-STD-498-documentation.html
.. _Celery\: Distributed Task Queue: http://www.celeryproject.org
.. _Google search for 'graphviz dot tutorial': http://www.google.com/search?q=graphviz%20dot%20tutorial
.. _MKDOCS\: DOCUMENTING PROJECTS WITH MARKDOWN: https://ep2015.europython.eu/conference/talks/mkdocs-documenting-projects-with-markdown
.. _Building Product Documentation with MkDocs: http://www.sitepoint.com/building-product-documentation-mkdocs/
.. _MkDocs: http://www.mkdocs.org/
.. _Static Site Generator: https://www.fullstackpython.com/static-site-generator.html
.. _An Introduction to Programming in Go: https://www.golang-book.com/public/pdf/gobook.0.pdf
.. _Git: http://git-scm.com
.. _Git tips from the trenches: https://ochronus.com/git-tips-from-the-trenches/
.. _Learn Git Branching: http://pcottle.github.io/learnGitBranching/?demo
.. _Git Interactive Rebase, Squash, Amend and Other Ways of Rewriting History: https://robots.thoughtbot.com/git-interactive-rebase-squash-amend-rewriting-history
.. _Git\: Using topic branches and interactive rebasing effectively: https://blog.mozilla.org/webdev/2011/11/21/git-using-topic-branches-and-interactive-rebasing-effectively/
.. _Git - When to Merge vs. When to Rebase: https://www.derekgourlay.com/blog/git-when-to-merge-vs-when-to-rebase/
.. _2.3 Git Basics - Viewing the Commit History: https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History
.. _gitk: https://git-scm.com/docs/gitk
.. _esc/git-big-picture: https://github.com/esc/git-big-picture
.. _Visualizing branch topology in git: http://stackoverflow.com/questions/1838873/visualizing-branch-topology-in-git
.. _kdiff3: http://kdiff3.sourceforge.net
.. _meld: http://meldmerge.org/
.. _Git merging using Meld: http://stackoverflow.com/questions/11133290/git-merging-using-meld
.. _Three way git merging with meld: https://lukas.zapletalovi.com/2012/09/three-way-git-merging-with-meld.html
.. _Painless Merge Conflict Resolution in Git: http://blog.wuwon.id.au/2010/09/painless-merge-conflict-resolution-in.html
.. _How to undo (almost) anything with Git: https://github.com/blog/2019-how-to-undo-almost-anything-with-git
.. _Undo Almost Anything with Git webinar: https://youtu.be/oUzbaCRoeFA
.. _Undoing Changes: https://www.atlassian.com/git/tutorials/undoing-changes
.. _GitHub: https://github.com
.. _Vincent Dreisen branching workflow: http://nvie.com/posts/a-successful-git-branching-model/
.. _Fork A Repo: https://help.github.com/articles/fork-a-repo/
.. _Forking Projects: https://guides.github.com/activities/forking/index.html
.. _Syncing a fork: https://help.github.com/articles/syncing-a-fork/
.. _Pushing to a remote: https://help.github.com/articles/pushing-to-a-remote/
.. _git-flow: http://danielkummer.github.io/git-flow-cheatsheet/
.. _Getting Started – Git-Flow: https://yakiloo.com/getting-started-git-flow/
.. _hub: https://hub.github.com/
.. _HubFlow: http://datasift.github.io/gitflow/
.. _Using GitFlow with GitHub: https://datasift.github.io/gitflow/GitFlowForGitHub.html
.. _Versioning: http://datasift.github.io/gitflow/Versioning.html
.. _GitHub Flow Like a Pro with these 13 Git Aliases: http://haacked.com/archive/2014/07/28/github-flow-aliases/
.. _Development flow with git flow, github: http://vysakh0.github.io/development-flow-with-git-flow-github/
.. _GitFlow\: safely merge develop changes to a feature branch: http://stackoverflow.com/questions/21661263/gitflow-safely-merge-develop-changes-to-a-feature-branch
.. _Comparing Workflows: https://www.atlassian.com/git/tutorials/comparing-workflows
.. _bumpversion: https://github.com/peritus/bumpversion
.. _bumpversion screencast: https://asciinema.org/a/3828
.. _A Python Versioning Workflow With Bumpversion: http://kylepurdon.com/blog/2015/01/25/a-python-versioning-workflow-with-bumpversion/
.. _PEP 440 -- Version Identification and Dependency Specification: http://legacy.python.org/dev/peps/pep-0440/
.. _Includes in your git config: http://agateau.com/2015/splitting-your-gitconfig/
.. _Using git's include for private configuration information (like github tokens): http://travisjeffery.com/b/2012/03/using-git-s-include-for-private-configuration-information-like-github-tokens/
.. _Protect Your Private Data Using Gitconfig Include Directive:
.. _One weird trick for powerful Git aliases: http://blogs.atlassian.com/2014/10/advanced-git-aliases/
.. _mwhite/git-aliases.md: https://gist.github.com/mwhite/6887990
.. _Must Have Git Aliases\: Advanced Examples: http://durdn.com/blog/2012/11/22/must-have-git-aliases-advanced-examples/
.. _mcxiaoke/.gitconfig: https://gist.github.com/mcxiaoke/6781994
.. _What are your favorite Git aliases?: https://m.reddit.com/r/git/comments/oje16/what_are_your_favorite_git_aliases/
.. _SCM Breeze: https://github.com/ndbroadbent/scm_breeze#scm-breeze-
.. _encrypted repositories?: http://thread.gmane.org/gmane.comp.version-control.git/123466/focus=123485
.. _AGWA/git-crypt: https://github.com/AGWA/git-crypt
.. _shadowhand/encrypted-git-repo.md: https://gist.github.com/shadowhand/873637
.. _7.14 Git Tools - Credential Storage: https://git-scm.com/book/en/v2/Git-Tools-Credential-Storage
.. _ndbroadbent/scm_breeze: https://github.com/ndbroadbent/scm_breeze
.. _Git on Mac OS X\: Don't ignore case!: http://tapestryjava.blogspot.com/2010/07/git-on-mac-os-x-dont-ignore-case.html
.. _How do I commit case-sensitive only filename changes in Git?: http://stackoverflow.com/questions/17683458/how-do-i-commit-case-sensitive-only-filename-changes-in-git
.. _Case sensitivity in Git: http://stackoverflow.com/questions/8904327/case-sensitivity-in-git
.. _version.py: https://gist.github.com/mina86/8782771
.. _How to delete files permanently from your local and remote git repositories: http://www.zyxware.com/articles/4027/how-to-delete-files-permanently-from-your-local-and-remote-git-repositories
.. _aaronzirbes/shrink-git-repo.sh: https://gist.github.com/aaronzirbes/4570924
.. _How to Shrink a Git Repository: http://stevelorek.com/how-to-shrink-a-git-repository.html
.. _Agile methodology: http://agilemethodology.org
.. _Scrum methodology: http://scrummethodology.com
.. _Jira Agile: https://www.atlassian.com/software/jira/agile
.. _Continuous Integration: http://www.thoughtworks.com/continuous-integration
.. _Jenkins CI: http://jenkins-ci.org/
.. _Pipeline as Code with Jenkins: https://jenkins.io/solutions/pipeline/
.. _GitHub Organization Folder Plugin: https://wiki.jenkins-ci.org/display/JENKINS/GitHub+Organization+Folder+Plugin
.. _Pipeline Stage View Plugin: https://wiki.jenkins-ci.org/display/JENKINS/Pipeline+Stage+View+Plugin
.. _JENKINS_HOME directory: https://wiki.jenkins-ci.org/display/JENKINS/Administering+Jenkins
.. _Distributed builds: https://wiki.jenkins-ci.org/display/JENKINS/Distributed+builds#Distributedbuilds-Example%3AConfigurationonUnix
.. _Simple Continuous Integration / Deployment With Jenkins: https://www.rdegges.com/2011/simple-continuous-integration-deployment-with-jenkins/
.. _7 Habits of Highly Effective Jenkins Users: http://www.slideshare.net/andrewbayer/7-habits-of-highly-effective-jenkins-users
.. _A Back Up And Restore Recipe for Jenkins Metadata: http://buildlackey.com/a-back-up-and-restore-recipe-for-jenkins-metadata/
.. _How To Deploy Jenkins Completely Pre-Configured - Automating Jenkins: https://blog.nimbleci.com/2016/10/11/how-to-deploy-jenkins-completely-pre-configured
.. _Jenkins2 Pipeline jobs using Groovy code in Jenkinsfile: https://wilsonmar.github.io/jenkins2-pipeline/
.. _Creating Jenkins pipelines with Ansible, part 1: https://wjoel.com/posts/ansible-jenkins-pipeline-part-1.html
.. _Creating Jenkins pipelines with Ansible, part 2: https://wjoel.com/posts/ansible-jenkins-pipeline-part-2.html
.. _GoCD: https://www.go.cd/
.. _Automatically Generating Jenkins Jobs: https://www.slalom.com/thinking/automatically-generating-jenkins-jobs
.. _What is DevOps?: http://theagileadmin.com/what-is-devops/
.. _Implementing Continuous Delivery\: Jenkins or Bamboo?: http://www.getzephyr.com/insights/implementing-continuous-delivery-jenkins-or-bamboo
.. _Introduction to Scrum - CollabNet Scrum Training Part 1: http://www.youtube.com/watch?v=D8vT7G0WATM&list=PLF6BFA8BAEDF6CE70
.. _Kronuz / celery: http://www.verious.com/code/Kronuz/celery/
.. _AMQP and Beyond\: Messaging by Extending RabbitMQ: http://www.rabbitmq.com/resources/ErlangFactorySFBay2010-TonyGarnock-Jones.pdf
.. _kombu - AMQP Messaging Framework for Python: http://zoomq.qiniudn.com/ZQScrapBook/ZqFLOSS/data/20110322223334/
.. _Postage - a RabbitMQ-based Component Python Library: http://lgiordani.github.io/blog/2013/07/25/postage-a-rabbitmq-based-component-python-library/
.. _Federated Queues: https://www.rabbitmq.com/federated-queues.html
.. _Distributed RabbitMQ brokers: https://www.rabbitmq.com/distributed.html
.. _Alvaro Videla - Building a Distributed Data Ingestion System with RabbitMQ: https://youtu.be/EUfSgYU_SFk
.. _Distributed log aggregation with RabbitMQ Federation: http://jaxenter.com/distributed-log-aggregation-with-rabbitmq-federation-107287.html
.. _Routing Topologies for Performance and Scalability with RabbitMQ: http://spring.io/blog/2011/04/01/routing-topologies-for-performance-and-scalability-with-rabbitmq/
.. _Configuring SSL for RabbitMQ: http://www.gettingcirrius.com/2013/01/configuring-ssl-for-rabbitmq.html
.. _Securing the RabbitMQ Management Console with SSL: http://www.gettingcirrius.com/2013/01/securing-rabbitmq-management-console.html
.. _Adventures in Lean: http://lostechies.com/derickbailey/2008/11/19/adventures-in-lean/
.. _44 engineering management lessons: http://www.defmacro.org/2014/10/03/engman.html
.. _Learn Scrum in 7 Minutes!: http://www.youtube.com/watch?v=kYajjGi5-qM
.. _Web scraping 101 with Python: http://www.gregreda.com/2013/03/03/web-scraping-101-with-python/
.. _How To Get Started With Kanban In Software Development: http://lostechies.com/derickbailey/2009/08/05/how-to-get-started-with-kanban-in-software-development/
.. _templatemaker: https://code.google.com/p/templatemaker/
.. _iPhone vs.  Evo: http://www.youtube.com/watch?v=DaxU0ut5tUw
.. _I Need Agile Methodology: http://www.youtube.com/watch?v=nvks70PD0Rs
.. _BeautifulSoup: http://www.crummy.com/software/BeautifulSoup/
.. _Semantic-Org/Semantic-UI: https://github.com/Semantic-Org/Semantic-UI
.. _The Stanford Parser\: A statistical parser: http://nlp.stanford.edu/software/lex-parser.shtml
.. _templater: https://pypi.python.org/pypi/templater/0.1.0
.. _"wrapper induction": http://scholar.google.com/scholar?q=wrapper+induction
.. _Kanban vs. Scrum\: Kanban is NOT for Software Development, but Scrum is!: http://scrumcrazy.wordpress.com/2013/02/04/kanban-vs-scrum-kanban-is-not-for-software-development-but-scrum-is/
.. _tl;dr Legal: http://www.tldrlegal.com/
.. _Apache 2.0 License: http://www.tldrlegal.com/license/apache-license-2.0-(apache-2.0)
.. _BSD 3-Clause License (Revised): http://www.tldrlegal.com/license/bsd-3-clause-license-(revised)
.. _Apache 2.0 and BSD 3-Clause Licenses (Merged): http://www.tldrlegal.com/compare?a=Apache+License+2.0+(Apache-2.0)&b=BSD+3-Clause+License+(Revised)
.. _How to Make Money from Open Source: http://hintjens.com/blog:27
.. _How To Capture an Open Source Project: http://hintjens.com/blog:68
.. _OSI Hopes To Decrease Number of Licenses: http://developers.slashdot.org/developers/05/02/16/2210209.shtml
.. _Understanding Open Source Software: http://www.groklaw.net/article.php?story=20031231092027900
.. _BSD and GPL Licensing: http://en.wikipedia.org/wiki/BSD_and_GPL_licensing
.. _The Open Source Initiative: http://www.opensource.org/
.. _Open Source Licensing\: Links and Resources: http://www.wasabisystems.com/gpl/links.html
.. _GPL v3 drafting process: http://gplv3.fsf.org/
.. _MySQL's "dual-license" model: http://www.mysql.com/company/legal/licensing/
.. _Trademark and OSS: http://www.law.washington.edu/lct/swp/Law/trademark.html
.. _Derivative Works: http://www.law.washington.edu/lct/swp/Law/derivative.html
.. _Patent Risks: http://www.law.washington.edu/lct/swp/Law/patents.html
.. _Dual Licensing: http://www.oss-watch.ac.uk/resources/duallicence.xml
.. _Dual Licensing in Open Source Software Industry: http://opensource.mit.edu/papers/valimaki.pdf
.. _Dual Licensing\: Having Your Cake and Eating It Too: http://www.linuxinsider.com/story/38172.html
.. _MySL AB FLOSS Exception: http://www.mysql.com/company/legal/licensing/foss-exception.html
.. _Litigation in Open Source: http://open-bar.org/docs/Open_Source_Litigation_8-2004.ppt
.. _Linksys routers caught up in open source dispute: http://searchnetworking.techtarget.com/originalContent/0,289142,sid7_gci932666,00.html
.. _Is Linksys shirking the GPL? (Maybe not.): http://www.oreillynet.com/pub/wlg/3580
.. _Linux's Hit Men: http://www.forbes.com/2003/10/14/cz_dl_1014linksys.html
.. _GPL\: IT'S THE LAW: http://www.open-mag.com/features/Vol_24/GPL/gpl.htm
.. _list of open source licenses: http://www.opensource.org/licenses/
.. _Automated Software Distribution Committee (ASDC): http://sundance.cso.uiuc.edu/dehaan/asd.html
.. _Automated Software Distribution at Sun Microsystems: http://www.eu.sun.com/sunservice/MANAGING/managing_case_studies.html#software
.. _Electronic Software Distribution\: A Long Shot: http://www.uniforum.org/news/html/publications/ufm/mar96/swdist.html
.. _FFive Projects: http://www.lsa.umich.edu/~ffive/proj/projects.html
.. _OSF DME Software Distribution Service: http://www.osf.org/comm/lit/DME-SDS-0593-1.html

.. _Useful one-line scripts for sed: http://sed.sourceforge.net/sed1line.txt
