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
            

 
        
