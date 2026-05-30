Uncompleted project...Best view in code atm.

updating notes


Notes:

on nexos run 
dir bootflash:
switch# dir bootflash:

 1856263168    Aug 24 08:19:17 2021  nxos64.10.2.1.F.bin

 Notes:

 Checking LEAF-A connectivity etc.... NOTES

 Check interfaces to spine 1 & 2 are up.

 leaf-a# sho ip int br

IP Interface Status for VRF "default"(1)
Interface            IP Address      Interface Status
Lo0                  172.16.0.2      protocol-up/link-up/admin-up       
Eth1/1               39.0.0.2        protocol-up/link-up/admin-up       
Eth1/2               60.0.0.2        protocol-up/link-up/admin-up  

leaf-a# show bgp sessions

Total peers 1, established peers 1
ASN 65000
VRF default, local ASN 65000
peers 1, established peers 1, local router-id 172.16.0.2
State: I-Idle, A-Active, O-Open, E-Established, C-Closing, S-Shutdown

Neighbor        ASN    Flaps LastUpDn|LastRead|LastWrit St Port(L/R)  Notif(S/R)
172.16.0.1      65000 0     00:06:52|00:00:23|00:00:51 E   51808/179        0/0


leaf-a# sho vlan

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    
10   VLAN00010                        active    
20   VLAN00020                        active    
50   VLAN00050                        active    

VLAN Type         Vlan-mode
---- -----        ----------
1    enet         CE     
10   enet         CE     
20   enet         CE     
50   enet         CE     

Remote SPAN VLANs
-------------------------------------------------------------------------------

Primary  Secondary  Type             Ports
-------  ---------  ---------------  -------------------------------------------



leaf-a# 
leaf-a# sho nve peers
Interface Peer-IP                                 State LearnType Uptime   Router-Mac       
--------- --------------------------------------  ----- --------- -------- ----------
nve1      172.17.0.2                              Up    CP        00:01:23 n/a  
            

leaf-b# sho nve peer
Interface Peer-IP                                 State LearnType Uptime   Router-Mac       
--------- --------------------------------------  ----- --------- -------- ----------
nve1      172.16.0.2                              Up    CP        00:00:10 n/a  

See what's in the VLAN from the NXOS leaf-a


 leaf-a# show mac address-table vlan 10
Legend: 
        * - primary entry, G - Gateway MAC, (R) - Routed MAC, O - Overlay MAC
        age - seconds since last seen,+ - primary entry using vPC Peer-Link,
        (T) - True, (F) - False, C - ControlPlane MAC, ~ - vsan,
        (NA)- Not Applicable
   VLAN     MAC Address      Type      age     Secure NTFY Ports
---------+-----------------+--------+---------+------+----+------------------
*   10     0050.0000.0d00   dynamic  NA         F      F    Eth1/12
C   10     0050.0000.1000   dynamic  NA         F      F    nve1(172.17.0.2)
*   10     0050.7966.6805   dynamic  NA         F      F    Eth1/10
*   10     0050.7966.6806   dynamic  NA         F      F    Eth1/11
C   10     0050.7966.6809   dynamic  NA         F      F    nve1(172.17.0.2)
C   10     0050.7966.680a   dynamic  NA         F      F    nve1(172.17.0.2)
C   10     5000.000e.0000   dynamic  NA         F      F    nve1(172.17.0.2)
*   10     5000.000f.0000   dynamic  NA         F      F    Eth1/13
G   10     5001.0000.1b08   static   -         F      F    sup-eth1(R)
leaf-a#


leaf-b# show mac address-table vlan 10
Legend: 
        * - primary entry, G - Gateway MAC, (R) - Routed MAC, O - Overlay MAC
        age - seconds since last seen,+ - primary entry using vPC Peer-Link,
        (T) - True, (F) - False, C - ControlPlane MAC, ~ - vsan,
        (NA)- Not Applicable
   VLAN     MAC Address      Type      age     Secure NTFY Ports
---------+-----------------+--------+---------+------+----+------------------
C   10     0050.0000.0d00   dynamic  NA         F      F    nve1(172.16.0.2)
*   10     0050.0000.1000   dynamic  NA         F      F    Eth1/13
C   10     0050.7966.6805   dynamic  NA         F      F    nve1(172.16.0.2)
C   10     0050.7966.6806   dynamic  NA         F      F    nve1(172.16.0.2)
*   10     0050.7966.6809   dynamic  NA         F      F    Eth1/10
*   10     0050.7966.680a   dynamic  NA         F      F    Eth1/11
*   10     5000.000e.0000   dynamic  NA         F      F    Eth1/12
C   10     5000.000f.0000   dynamic  NA         F      F    nve1(172.16.0.2)
G   10     5002.0000.1b08   static   -         F      F    sup-eth1(R)
leaf-b# 



        
