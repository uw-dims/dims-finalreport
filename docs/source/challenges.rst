.. _challenges:

Challenges Encountered
======================

.. _staffingchallenges:

Staffing Challenges
-------------------

The document :ref:`dimsjds:dimsjobdescriptions` was produced to list
the full set of skills and experience required by those working on a
project of this nature.


.. _dnschallenges:

DNS Challenges
--------------

Naming Computers
~~~~~~~~~~~~~~~~

Naming computers is not easy. One of the tenets of security is separation
of services, which historically drove system administrators to limit
services to one per computer. In that light, naming a computer based on
the service it provides seems to make sense. Until you decide to add
more services to that computer, at which point one of two things
happens:

#. The computer's name now only matches one of the two services, and
   it becomes harder to know what computer name to use when trying to
   connect to the second service. ("The Git repos are on ``git``, and
   Jira is on ``jira``. We put Jenkins on one of those two servers,
   but was it ``git`` or ``jenkins``?).

#. The service is put on another computer (possibly a virtual machine)
   and the computer's name now matches the service. But now there is also
   another computer host to manage, with ``iptables`` rules, accounts and
   passwords, the need to copy in SSH keys, etc. As more computers are added,
   management and use gets harder and harder.

Part of this problem is handled by *not* naming computers after
services, but instead using more generic host names. Those host names
are then mapped with DNS *A* records (and associated *PTR* records
to properly reverse-map the IP to name). The use of CNAME entries can now
create aliases in DNS name space, allowing URLs to be formed with the
service name as part of the DNS name.

The drawback to this is that the administration of A records, PTR records, and
CNAMES is more difficult than simple ``/etc/hosts`` entries, and requires a
deeper understanding of DNS internals by all involved.

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

Yet one more issue that complicates connectivity is
the use of mobile devices like laptops, which must use a
VPN to connect to access-controlled hosts behind firewalls.
If split-horizon DNS is used, with one DNS server behind
the VPN such that it is only accessible when the VPN is
connected, the mobile device may experience significant
delays in DNS requests that cannot be sent to the unavailable
DNS server. This requires complicated dynamic DNS resolver
configuration that is difficult to set up and to debug
without expertise in advanced network configuration on
the operating system being used (in this case, Mac OS X
and Ubuntu Linux were the two predominant operating
systems on laptops.)

.. _distributedchallenges:

Distributed Systems Challenges
------------------------------

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

.. _abstractionchallenges:

Challenges with Abstraction
---------------------------

Related to the :ref:`distributedchallenges` are challenges related
to abstraction. Abstraction presents challenges in many ways.

#. The presence of an abstraction layer may create opacity (i.e.,
   things behave like a *black box* and either work or fail, with
   little feedback). This requires greater expertise in debugging.
   
#. The lack of an abstraction layer requires more direct connections
   between *caller* and *callee* in programs, or between *connector* and
   *connectee* in TCP/IP socket connections. This directness seems
   simple at first, but in the face of a large number of connections
   or calls, it becomes very difficult to add each new connection, to
   make changes, or to debug when one of a large number of similar
   looking connections fails.

#. The lack of an abstraction layer also makes it harder to support
   versioning of APIs, since more direct calls are being made
   and things like changes in function names or changes in
   IP addresses, DNS names, or TCP/IP ports.

One place where abstraction comes in handy is providing a standard
application programming interface (API) that takes a simple set of
parameters in a function call, but hides the underlying details of
where data is obtained prior to being returned to the caller in
a single data structure. The Trident portal holds a limited set of
attributes about a user, but some programs integrated into DIMS
need more attributes. That means one of two things must happen:

#. Trident is modified support the extra attributes that are needed, or

#. An abstration layer is added that makes one call to Trident to
   get the attributes it holds, and a second call to a DIMS database
   component to get the extra attributes, combining them into one
   data structure and returning that to the caller.

This is illustrated in the following whiteboard sketch:


.. figure:: images/user-attributes.jpg
   :width: 50%
   :alt: user-attributes.jpg
   :align: center
   :name: user-attributes.jpg

   user-attributes.jpg

..

