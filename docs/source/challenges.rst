.. _challenges:

Challenges Encountered
======================

.. _toolknowledge:

Understanding the Tools Being Used
----------------------------------

It is a myth that humans only use 10% of their brain. [1]_ But it is
common for programmers and system administrators to only learn a
small portion of the features and capabilities of any given program
or tool that they may need to use. The simple thing to do is go search
`StackExchange`_ for system administration tasks, or `StackOverflow`_
for programming tasks, and simply copy/paste what someone posts there
in order to quickly "solve" the problem at hand and move on to the
next thing.

.. _StackExchange: http://unix.stackexchange.com/
.. _StackOverflow: http://stackoverflow.com/

Taking this kind of a short-cut, bypassing the time investment to learn
(or at the very minimum, familiarizing oneself with the content of
available documentation by skimming through it completely) can result
in problems later on. Scripts may be written that restrict or limit
the utility of the program being called, or that perform extra
work that could be done in a more straight-forward or idiomatic way
using advanced features of the tool in question. When someone is
tasked with solving a particular problem, given a set of requirements
or use cases that should be satisfied, it is important that they
take on the responsibility of studying the tool being used to
understand how best to use it.

.. _staffingchallenges:

Staffing Challenges
-------------------

The document :ref:`dimsjds:dimsjobdescriptions` was produced to list the full
set of skills and experience required by those working on a project of this
nature. It can be safely stated that every member of the team was pushed beyond
their technical limits and had to constantly research and learn new
technologies and rapidly acquire new software engineering, network engineering,
or system administration skills. Not everyone is capable (or happy) when pushed
beyond their limits and some turnover on the project was directly related to
this pressure to deliver.

Over the course of the project, the team size was typically 3-5 people, with
most of the team working at less than 100% FTE. (One contractor was 100% FTE
for the majority of the project and had to step in to perform tasks that were
not being performed by other team members.  At several portions of the project,
the PI was at 50% FTE in terms of the project budget, but often worked 60-80
hours per week, sometimes more, to ensure that tasks were completed to meet
deliverable deadlines.)

The team was also partially virtual, with one, two, and sometimes three
staff members working on the East Coast, while the rest of the team was
on the West Coast. One sub-contractor was located in California. Regular
"scrum" meetings were held using online tools (at various times Adobe
Connect, Skype, and Google Hangout were all used, to varying degrees of
effectiveness or frustration.) This made the problem of trying to bring
team members up to speed on new concepts and skills difficult, due
to lack of physical presense and availability.

.. _dnschallenges:

DNS Challenges
--------------

Naming Computers
~~~~~~~~~~~~~~~~

Naming computers is not easy. One of the tenets of secure design is
*separation of services*, which historically has driven system
administrators to limit services to one service per computer. You have a DNS
server that does DNS, a database server for data storage, a web server
that provides HTTP/HTTPS service to browsers, an FTP file server that
only serves static files, etc.

In such simple deployments, naming a computer based on the service it
provides seems to make sense and to be simple. Until you decide to it
makes more sense to combine some related services on that one
computer, at which point one of two things happens:

#. The computer's name now only matches one of the two services, and
   it becomes harder to know what computer name to use when trying to
   connect to the second service. ("The Git repos are on ``git``, and
   Jira is on ``jira``. We put Jenkins on one of those two servers,
   but was it ``git`` or ``jenkins``?).

#. The service is put on another computer (possibly a virtual machine)
   and the computer's name now matches the service. But now there is also
   another computer host to manage, with ``iptables`` rules, accounts and
   passwords allowing adminstrator access, the need to copy in SSH keys, etc.
   As more computers are added, management and use gets harder and harder.

Part of this problem is handled by adopting a policy of *not* naming computers after
services, but instead using more generic host names (like colors like
``red`` and ``orange``, or generic names like ``node01`` through ``node09``).
Those host names are then mapped with DNS *A* records (and associated *PTR* records
to properly reverse-map the IP to name) and using CNAME entries that
create aliases in DNS name space, allowing URLs to be formed with the
service name as part of the DNS name. (E.g., ``trident.devops.local``
may map to ``yellow.devops.local`` via a CNAME).

The drawback to this is that the administration of A records, PTR records, and
CNAMES is more difficult than simple ``/etc/hosts`` entries, and requires a
deeper understanding of DNS internals by all involved. The final implementation
of DIMS Ansible playbooks generates DNS host name mappings using Jinja
templating to generalize creating DNS entries.

Another problem that must be dealt with when placing multiple services on
the same system is TCP port mappings. You can only have one service listening
to port ``80/tcp``, port ``443/tcp``, etc. That requires that services like
Trident, a web application service, etc., all have their own unique high-numbered
service ports (e.g., ``8080/tcp`` for Trident, ``8000/tcp`` for the web
application service, ``8500/tcp`` for Consul's UI, etc.) But now how do
you remember which port to use to get to which service on which host?
Adopting a prefix with the service's name and using a CNAME that aliases
the host allows an easier to remember mechanism to reach services,
though at the cost of complexity in NGINX reverse proxy configuration.
You can now access Trident using ``https://trident.devops.local/trident``
and ``https://consul.devops.local/consul`` to get to the Consul UI.
What is more, using multiple DNS records for each Consul node in
a cluster allows for round-robin access to distribute the connections
across cluster nodes:

.. code-block:: none

   $ dig consul.devops.local +short
   192.168.56.23
   192.168.56.21
   192.168.56.22

..

Separating DNS Name Spaces
~~~~~~~~~~~~~~~~~~~~~~~~~~

Adding to the complexity of DNS and host naming is the situation of
multi-homed hosts. Most people are used to one computer with one
or two interfaces (like a laptop with either a wired Ethernet
interface, or a WiFi interface, only one of which is active at any
given time). That means the computer always has just one active
IP address, and since laptops are usually used for connecting as
a client to remote services, don't even need to have a DNS name!

Layered, segmented networks that involve external firewalling,
Virtual Private Network (VPN) access to multi-segmented Virtual
Local Area Network (VLAN) switched or virtual machine network
environments cause problems when it comes to host naming
and DNS naming.

The way that multi-homed network namespace management is handled
is through the use of *Split horizon* (or *split-brain*) DNS.
This requires multiple DNS servers, multiple DNS zones,
and careful mapping of the IP addresses and DNS names for
each of the zones, as necessary to route packets properly
through the correct interface. Again, this requires a much
deeper understanding of DNS than is common.


Handling Dynamic Addressing on Mobile Devices
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Yet one more issue that complicates connectivity is the use of mobile devices
like laptops, which must use a VPN to connect to access-controlled hosts behind
firewalls.  If split-horizon DNS is used, with one DNS server behind the VPN
such that it is only accessible when the VPN is connected, the mobile device
may experience significant delays in DNS requests that cannot be sent to the
unavailable DNS server. This requires complicated dynamic DNS resolver
configuration that is difficult to set up and to debug without expertise in
advanced network configuration on the operating system being used (in this
case, Mac OS X and Ubuntu Linux were the two predominant operating systems on
laptops.)

One of the ramifications of mobile devices using Ubuntu Linux is the
role of ``NetworkManager``, a notoriously problematic service in
terms of network configuration management. It is very difficult to
take control of services like ``dnsmasq`` for split-horizon DNS,
or use VPNs (especially multiple VPNs, as was implemented in this
project from the start), without running into conflicts with
``NetworkManager``.

The DIMS project started using the Consul service as a means of
registering the IP address of a client using a VPN, such that
the current address and accessibility status is available using
Consul's DNS service. As Consul was going to be used for service
health monitoring as well, this seemed like a good choice. One
downside is further complexity in DNS handling, however, since
not all hosts in the deployment were configured to run Consul
using Ansible playbooks.

.. _distributedchallenges:

Distributed Systems Challenges
------------------------------

There are several challenges to building even a small-scale distributed
system compromising multiple operating systems on multiple network
segments with multiple layers of baremetal, virtual machine, and/or
containerization.

.. _physicalDistribution:

Physical Distribution
~~~~~~~~~~~~~~~~~~~~~

One of the core challenges when building distributed systems results
from using separate DNS host names and physically separate data centers
and/or logically separated subnets.

At the start of the DIMS project, hardware was physically located in two server
rooms in two separate buildings operated by the Applied Physics Laboratory,
with staff being located on a separate floor in one of the buildings. What
is more, some staff had computers using static IP addresses with direct
access to the internet, while others used dynamic IP addresses behind
a separate APL "logical firewall" device. This meant use of four separate
IP address ranges on four subnets behind two different firewalls. Other
hardware was located in the main UW Data Center in the UW Tower building
on a fifth network. Add to this one hypervisor on a system in the APL
server room and another in the UW Tower, each with a separate OpenVPN
server, with the necessity to route traffic between virtual machines
on the two hypervisors. (Both hypervisors, by the way, were different
and ran on two different operating systems.)

On multiple occassions, hardware had to be moved from one location
to another (which meant changing IP addresses on both bare-metal
hosts and virtual machines, changing routes, and changing VPNs.)
The last time hardware was moved, this time to consolidate it all
into one data center, everything broke.

One of the machines being moved served as the hypervisor for approximately
a dozen virtual machines making up the core of the DIMS development
environment. At least three previous attempts were made to task team members
with documenting the "as-built" configuration of all of these components,
their IP addresses and routes, and mechanisms for remote control,
in order to plan for the configuration changes needed to perform the move.
Each previous time a move had been planned it had to be
put off because higher priority tasks needed to be addressed and/or team
members had left the project before they had completed the tasks necessary for
migration. When the hardware finally had to be hastily moved due to the
impending extended leave of a key participant, the hastily performed move
caused the entire DIMS network to become non-functional and the PI and two team
members spent the next five days working to get the system functional and
stable again.  This process revealed that the configuration of the DIMS systems
was significantly below the quality level previously assumed.  System
configuration settings were not adequately documented, were almost entirely
hand-crafted (as opposed to being under Ansible configuration control as was
specified), used two different hypervisors (KVM and Virtualbox) on two
different operating systems (RedHat Enterprise Linux 6 and Debian) and the
networking relied heavily on something known as `Project 172 private address
routing`_ combined with internal virtual networks that were administered by
just one former team member using remote desktop services and/or X11 forwarding
from a workstation that was no longer available as an option to use. The
instability and outages caused by this long-delayed (yet required) hardware
move set the team back significantly and had ripple effects on other deadlines
and events that could not be adjusted or cancelled.

.. _Project 172 private address routing: https://itconnect.uw.edu/connect/uw-networks/network-addresses/private-address-routing/

.. _stability:

Stability
~~~~~~~~~

Due to the inherent inter-relationships between subcomponents in a distributed
system, stability of the overall system is a constant challenge.
Not only are hardware moves like those described in the previous section a
contributor to instability, but so are software changes.

As the DIMS project is using open source operating systems and tools that may
be updated on as frequent as a monthly basis, often resulting in parts of
the system "breaking" when an update happens.

[ Container Linux ...]

[ Configuration changes, such as the change to Trident's style sheets. ]

.. _abstractionchallenges:

Challenges Related to Abstraction
---------------------------------

Related to the :ref:`distributedchallenges` are challenges related
to abstraction. Abstraction presents challenges in many ways.

#. The presence of an abstraction layer in code and service connections
   may create opacity (i.e., things behave like a *black box* and either work
   or fail, with little feedback). This requires greater expertise in
   debugging.

#. Abstration in service oriented architecture requires a greater level of
   expertise in configuring and debugging systems in that it is necessary
   for someone to be able to understand and control the system at any
   level in the abstrated stack, or to be able to jump up and down
   the application stack in order to diagnose and debug the system
   when something does not work. If someone is only capable of understanding
   the highest layer in the abstrated stack and something does not work,
   they must rely on someone else who has expertise at the lower layers
   in order to debug and fix any problems. (This is related to the
   issue of *opacity* in the system, or the *black box* effect).

#. The lack of an abstraction layer requires more direct connections between
   *caller* and *callee* in programs, or between *connector* and *connectee* in
   TCP/IP socket connections. This directness seems simple at first, but in the
   face of a large number of connections or calls, it becomes very difficult to
   add each new connection, to make changes, or to debug when one of a large
   number of similar looking connections fails.

#. The lack of an abstraction layer also makes it harder to support
   versioning of APIs, since more direct calls are being made
   and things like changes in function names or changes in
   IP addresses, DNS names, or TCP/IP ports.

One place where abstraction comes in handy is providing a standard application
programming interface (API) that takes a simple set of parameters in a function
call, but hides the underlying details of where data is obtained prior to being
returned to the caller in a single data structure. The Trident portal holds a
limited set of attributes about a user, but some programs integrated into DIMS
need more attributes. That means one of two things must happen:

#. Trident is modified support the extra attributes that are needed, or

#. An abstration layer is added that makes one call to Trident to
   get the attributes it holds, and a second call to a DIMS database
   component to get the extra attributes, combining them into one
   data structure and returning that to the caller.

This is illustrated in the following whiteboard sketch:

.. _figUserAttributes:

.. figure:: images/user-attributes.jpg
   :width: 50%
   :alt: user-attributes.jpg
   :align: center
   :name: user-attributes.jpg

   user-attributes.jpg

..

Related to abstraction is the classification of system components using
a taxonomy. A DIMS deployment is made up of a dozen or more computers
(be they bare metal or virtual machines). Each of these computers must
share a network address range, a segmented network topology with a VPN
for remote access, have domain names to map to IP addresses, have a
branded logo, etc. If a second DIMS instance is to be stood up, a
complete set of similar systems (though configured differently with
another address range, another set of DNS names, etc.) must be
independantly set up. This means that very little can be hard-coded,
since each deployment will be isolated and independent (yet made up
of the same service components from the same set of Ansible playbooks
and instructions). This isn't the way that most people learn how to
set up computers, so this presents both a conceptual challenge, as
well as an engineering challenge to separate configuration and code
that uses variables from the values that those variables take on
at run time (and to keep multiple sets of those variables separated
and organized so they don't interfere.)

.. [1] All You Need to Know About the 10 Percent Brain Myth, in
   60 Seconds, by Christian Jarrett, July 24, 2014.

.. _swengchallenges:

Software Engineering Challenges
-------------------------------

.. todo::

    Talk about coupling, cohesion,
