---
layout: default
title: Ryu Certification - ovs - config
---
# [Ryu Certification](http://osrg.github.io/ryu/certification.html)
* ovs 

# OpenFlow related configuration
<pre>
$ sudo ovs-vsctl show
ee1cf17b-6d5a-4b1a-9882-3c60d227b35e
    Bridge br0
        Controller tcp:10.24.150.30
        fail_mode: secure
        Port eth23
            Interface eth23
        Port eth22
            Interface eth22
        Port eth21
            Interface eth21
        Port br0
            Interface br0
                type: internal

$ sudo ovs-vsctl list Bridge | grep -v '\[\]' | grep -v '{}'
_uuid               : c023f004-01ac-40aa-8cd5-e01476fcf8d5
controller          : [11b3b3ba-43dd-41ea-98a3-16f33f3cdb95]
datapath_id         : 0000000000000001
datapath_type       : netdev
fail_mode           : secure
name                : br0
other_config        : {datapath-id=0000000000000001}
ports               : [5b127a17-495f-4538-9ae3-946340d42470, 946c1691-bcdb-4617-8f10-2e03b3fe594c, f8cde838-178d-4b7b-aab2-a334e4892a80, fc5b6836-4d58-4cff-94bf-b7c0222b1ce1]
protocols           : [OpenFlow14]
stp_enable          : false

$ sudo ovs-vsctl list Controller | grep -v '\[\]' | grep -v '{}'
_uuid               : 11b3b3ba-43dd-41ea-98a3-16f33f3cdb95
is_connected        : false
role                : other
status              : {last_error=Connection refused, sec_since_disconnect=2, state=BACKOFF}
target              : tcp:10.24.150.30

$ sudo ovs-vsctl list Port | grep -v '\[\]' | grep -v '{}'
_uuid               : f8cde838-178d-4b7b-aab2-a334e4892a80
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [dbdd4a0b-82db-458d-a041-e45509a9a2cc]
name                : eth21

_uuid               : 946c1691-bcdb-4617-8f10-2e03b3fe594c
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [293ce6c2-bdd9-46bb-9ef5-af78daecb095]
name                : eth22

_uuid               : fc5b6836-4d58-4cff-94bf-b7c0222b1ce1
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [0576dd0c-84d7-439b-973c-1b1f3fcde81e]
name                : br0

_uuid               : 5b127a17-495f-4538-9ae3-946340d42470
bond_downdelay      : 0
bond_fake_iface     : false
bond_updelay        : 0
fake_bridge         : false
interfaces          : [70ccad38-18dd-4d8d-a044-96662d08dc96]
name                : eth23

$ sudo ovs-vsctl list Interface | grep -v '\[\]' | grep -v '{}'
_uuid               : 70ccad38-18dd-4d8d-a044-96662d08dc96
admin_state         : up
duplex              : full
ifindex             : 25
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5e
mtu                 : 1550
name                : eth23
ofport              : 3
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1580216080, tx_dropped=0, tx_errors=0, tx_packets=9644096}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : 0576dd0c-84d7-439b-973c-1b1f3fcde81e
admin_state         : down
duplex              : full
ifindex             : 578
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 10000000
link_state          : down
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1500
name                : br0
ofport              : 65534
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=tun, driver_version=1.6, firmware_version=N/A}
type                : internal

_uuid               : 293ce6c2-bdd9-46bb-9ef5-af78daecb095
admin_state         : up
duplex              : full
ifindex             : 24
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5d
mtu                 : 1550
name                : eth22
ofport              : 2
statistics          : {collisions=0, rx_bytes=0, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=0, tx_bytes=1910398133, tx_dropped=0, tx_errors=0, tx_packets=27083818}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 

_uuid               : dbdd4a0b-82db-458d-a041-e45509a9a2cc
admin_state         : up
duplex              : full
ifindex             : 23
ingress_policing_burst: 0
ingress_policing_rate: 0
link_resets         : 0
link_speed          : 1000000000
link_state          : up
mac_in_use          : 00:60:e0:56:53:5c
mtu                 : 1550
name                : eth21
ofport              : 1
statistics          : {collisions=0, rx_bytes=1242933441, rx_crc_err=0, rx_dropped=0, rx_errors=0, rx_frame_err=0, rx_over_err=0, rx_packets=55335022, tx_bytes=0, tx_dropped=0, tx_errors=0, tx_packets=0}
status              : {driver_name=igb, driver_version=3.2.10-k, firmware_version=2.10-9}
type                : 
</pre>

# Version information
<pre>
$ git log -1 --pretty=fuller
commit 8faeab7257a28ccf3a13d2e823cef83feabbb44c
Author:     Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
AuthorDate: Mon Jun 23 04:39:47 2014 +0000
Commit:     Joe Stringer &lt;joestringer@nicira.com&gt;
CommitDate: Mon Jun 23 09:44:16 2014 +1200

    Makefile.am: fix printf-check in out-of-tree build
    
    The introduction of a %zu in datapath/flow_netlink.c with commit c1fc1411
    revealed a problem with out-of-tree builds.
    
    printf-check and thread-safety-check skip some directories with a 'grep -v'.
    In the case of an out-of-tree build, the grep -v pattern doesn't work, because
    it assumes the pathnames to be relative to the OVS root directory.
    
    This commit fixes the problem by changing the directory before executing any
    commands, like we do elsewhere in Makefile.am
    
    Signed-off-by: Daniele Di Proietto &lt;ddiproietto@vmware.com&gt;
    Signed-off-by: Joe Stringer &lt;joestringer@nicira.com&gt;
</pre>
