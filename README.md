# EtherChannel-Lab

A Layer 2 lab that bundles three physical links between two Cisco switches into a single logical EtherChannel. The bundle gives more bandwidth and redundancy, and STP treats it as one link, so no ports are blocked.


Topology
Device	Interface	Connected To
Sw1	Fa0/1 - Fa0/3	Sw2 Fa0/1 - Fa0/3 (EtherChannel, Port-channel 1)
Sw1	fa0/24 Access port	PC0
Sw2	Fa0/1 - Fa0/3	Sw1 Fa0/1 - Fa0/3 (EtherChannel, Port-channel 1)
Sw2	fa0/24 Access port	PC1


Configuration

Apply the same configuration on Sw1 and Sw2:

interface range FastEthernet0/1 - 3
 channel-group 1 mode active
 no shutdown

interface Port-channel1
 switchport mode trunk




Verification
show etherchannel summary
show interfaces port-channel 1
show spanning-tree
