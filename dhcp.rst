DHCP
****
Dynamic Host Configuration Protocol (DHCP) is a protocol used by machines to automatically configure themselves with an IP address and other related network information.  It relies on a central server to hand out temporary leases which correspond to an IP address.  DHCP leases can contain other information, such as fields needed to PXE boot.  DHCP is implemented using port 67 and 68.


Protocol
========

* DHCP requests begin with a client broadcasting a DHCPDISCOVER packet onto the network
* The DHCP server responds with a unicast packet containing a DHCPOFFER
* The client responds with a unicast packet containing a DHCPREQUEST
* The server responds with a DHCPACK

DHCP Helper
===========
As DHCP relies on a single broadcast packet in order to start the process, it generally does not work outside of the same Layer 2 broadcast domain.  Some network devices are able to work around this issue by using a feature called DHCP helper.  This allows the switch/router to receive the DHCP requests,  and forward them (unicast) to a DHCP server outside of the current network.  This feature means that you can run one DHCP server for an entire network, and not have to have the DHCP be present on every VLAN.

DHCP Helper requires a managed network device.  Not all vendors support this.

To configure DHCP helper for most Brocade devices, use:

.. code-block :: none

    ip dhcp snooping vlan 100
    !
    interface ve 100
        ip helper-address 1 <DHCP SERVER>
    !

To configure DHCP helper for most Cisco devices, use:

.. code-block :: none

    interval Vlan100
        ip helper-address <DHCP SERVER>
    !


Tools: ISC dhcpd
================




Defining classes, leases
========================

Options
=======

Default gateway
---------------

DNS server(s)
-------------
(Tie in previous chapters re: TFTP, PXE with related options?)



