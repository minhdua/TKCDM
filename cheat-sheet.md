# Task 1: Configure Cisco Router Global Configuration Settings.

## Step 1: Physically connect devices.

## Step 2: Connect host computer to router through HyperTerminal.
- no 
- Router> enable

## Step 3: Configure global configuration hostname setting.
- Router# configuration terminal
- router(config)# hostname Router1

## Step 4: Configure the MOTD banner.
- Router1(config)# banner ? 
- Router1(config)# banner motd %
```
Enter TEXT message.  End with the character '%'
***You are connected to an ABC network device. Access is granted to only current ABC company system administrators with prior written approval. ***

*** Unauthorized access is prohibited, and will be prosecuted. ***

*** All connections are continuously logged. ***

%
```

# Task 2: Configure Cisco router password access.

## Step 1: Configure the privileged exec password.
- Router1(config)# enable secret cisco

## Step 2: Configure the console password.
- Router1(config)# line console 0
- Router1(config-line)# password class
- Router1(config-line)# login


## Step 3: Configure the virtual line password.
- Router1(config-line)# line vty 0 4
- Router1(config-line)# password class
- Router1(config-line)# login
- Router1(config-line)# exit
- Router(config-line)#logging synchronous
- R1(config-if)#description
*Mar  1 01:28:04.242: %LINK-3-UPDOWN: Interface FastEthernet0/0, changed state to up
*Mar  1 01:28:05.243: %LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/0, changed state to up
- R1(config)#line console 0
- R1(config-line)#logging synchronous
- R1(config-line)#line vty 0 4
- R1(config-line)#logging synchronous
- Router(config-line)#exec-timeout minutes [seconds]
# Task 3: Configure Cisco Router Interfaces.

## Step 1: Configure the router fa0/0 interface.
- Router1(config)# interface fa0/0
- Router1(config-if)# description Connection to Host1 with crossover cable
- Router1(config-if)# ip address address mask
- Router1(config-if)# no shutdown

- Router1(config-if)# end

## Step 2: Configure the router Fa0/1 interface.
- Router1(config)# interface fa0/1
- Router1(config-if)# description Connection to switch with straight-through cable
- Router1(config-if)# ip address address mask
- Router1(config-if)# no shutdown
- Router1(config-if)# end

# Step 3: Configure the host computer.
- IP Address:  The first host address 
- Subnet Mask: The subnet mask 
- Default Gateway: Router’s IP Address 

# Task 4: Save the Router Configuration File.

## Step 1: Compare router RAM and NVRAM configurations.
- Router1# show startup-config
- Router1#show running-config

## Step 2: Save RAM configuration to NVRAM.
- copy running-config startup-config

# Task 5: Configure a Cisco Switch.

## Step 1: Connect the host to the switch.

## Step 2. Configure global configuration hostname setting.
- Switch> en
- Switch# config t
- Switch(config)# hostname Switch1

## Step 3: Configure the MOTD banner.
- Switch1(config)# banner motd %

## Step 4: Configure the privileged exec password.
- Switch1(config)# enable secret cisco

## Step 5: Configure the console password.
- Switch1(config)# line console 0
- Switch1(config-line)# password class
- Switch1(config-line)# login

## Step 6: Configure the virtual line password.
	
- Switch1(config-line)# line vty 0 15
- Switch1(config-line)# password class
- Switch1(config-line)# login

## Step 7: Configure the interface description.
- Switch1(config)# interface fa0/1
- Switch1(config-if)# description Connection to Router1
- Switch1(config)# interface fa0/2
- Switch1(config-if)# description Connection to host computer 2
- Switch1(config)# interface fa0/3
- Switch1(config-if)# description Connection to host computer 3
- Switch1(config-if)# end
## Step 8: Save RAM configuration to NVRAM.
- Switch1# copy run start
Task 3: Interpreting Debug Output.
# Task 3: Interpreting Debug Output.

## Step 1: On R1 from privileged EXEC mode, enter the debug ip routing command.
- R1#debug ip routing

## Step 2: Enter interface configuration mode for R1’s LAN interface.

## Step 3: Enter the command necessary to install the route in the routing table. 

## Step 4: Enter the command to verify that the new route is now in the routing table. 
- R1# show ip route

## Step 5: Enter interface configuration mode for R1’s WAN interface connected to R2.
- R1#configure terminal
- R1(config)#interface Serial 0/0/0
- R1(config-if)#ip address 172.16.2.1 255.255.255.0
- R1(config-if)#clock rate 64000
- R1(config-if)#no shutdown
- R2#debug ip routing
- R2#configure terminal
- R2(config)#interface serial 0/0/0
- R2(config-if)#ip address 172.16.2.2
 255.255.255.0
- R2(config-if)# no shutdown
- R1(config-if)# end
- R1# show ip route
- R2# show ip route

## Step 11: Turn off debugging on both routers using either no debug ip routing or simply, undebug all.
- R1#no debug ip routing

# Task 5: Configure IP Addressing on the Host PCs.

## Step 1: Configure the host PC1.

## Step 2: Configure the host PC2.

## Step 3: Configure the host PC3.

# Task 6: Test and Verify the Configurations.

## Step 1: Test connectivity.

## Step 2: Use the ping command to test connectivity between directly connected routers.

## Step 3: Use ping to check connectivity between devices that are not directly connected.

# Task 7: Gather Information.

## Step 1: Check status of interfaces.
- R2#show ip interface brief

## Step 2: View the routing table information for all three routers.
- R1# show ip route
- R2# show ip route
- R3# show ip route

# Task 8: Configure a Static Route Using a Next-Hop Address.

## Step 1: To configure static routes with a next-hop specified, use the following syntax:
- Router(config)# ip route network-address subnet-mask ip-address
- R3# show ip route

## Step 3: Use ping to check connectivity between the host PC3 and the host PC2. 

## Step 4: On the R2 router, configure a static route to reach the 192.168.2.0 network. 
- R2(config)#ip route 192.168.2.0 255.255.255.0 192.168.1.1

## Step 5: View the routing table to verify the new static route entry. 

## Step 6: Use ping to check connectivity between the host PC3 and the host PC2. 

# Task 9: Configure a Static Route Using an Exit Interface
- Router(config)# ip route network-address subnet-mask exit-interface
- R3(config)# ip route 172.16.2.0 255.255.255.0 Serial0/0/1
- R3# show ip route
- R3#show running-config

## Step 3: On the R2 router, configure a static route.
- R2(config)# ip route 172.16.3.0 255.255.255.0 Serial0/0/0

Step 4: View the routing table to verify the new static route entry.
- R2#_show ip route

Step 5: Use ping to check connectivity between the host PC2 and PC1.

# Task 10: Configure a Default Static Route.

## Step 1: Configure the R1 router with a default route.

- R1(config)#ip route 0.0.0.0 0.0.0.0 172.16.2.2

## Step 2: View the routing table to verify the new static route entry.
- R1# show ip route

## Step 3: Use ping to check connectivity between the host PC2 and PC1.

# Task 11: Configure a Summary Static Route.

## Step 1: Configure the summary static route on the R3 router. 
R3(config)#ip route 172.16.0.0 255.255.252.0 192.168.1.2

## Step 2: Verify that the summary route is installed in the routing table.
- R3#show ip route

## Step 3: Remove static routes on R3.
- R3(config)#no ip route 172.16.1.0 255.255.255.0 192.168.1.2 
- R3(config)#no ip route 172.16.2.0 255.255.255.0 Serial0/0/1  

## Step 4: Verify that the routes are no longer in the routing table.
- R3# show ip route 

## Step 5: Use ping to check connectivity between the host PC3 and PC1. 

# Configure a Summary Static Route from ISP to internal networks.
- ISP(config)#ip route 192.168.0.0 255.255.248.0
 209.165.200.2

# Configure RIPv2

## Configure RIPv2 on R1.
- R1(config)# ip route 0.0.0.0 0.0.0.0 s0/0/1
- R1(config)# router rip
- R1(config-router)# version 2
- R1(config-router)# no auto-summary
- R1(config-router)# network 192.168.1.0
- R1(config-router)# network 192.168.2.0
- R1(config-router)# passive-interface gig 0/0
- R1(config-router)# default-information originate

## Configure RIPv2 on R2.

## Configure RIPv2 on R3

# Verify Configurations

## View routing tables of R1, R2, and R3.

## Verify full connectivity to all destinations.
-----

# Task 1: Prepare the Network.

## Step 1: Cable a network that is similar to the one in the Topology Diagram. 

## Step 2: Clear any existing configurations on the routers.

# Task 2: Perform Basic Router Configurations.

# Task 3: Configure and Activate Serial and Ethernet Addresses.

## Step 1: Configure interfaces on R1, R2, and R3.

## Step 2: Verify IP addressing and interfaces.
- show ip interface brief

## Step 3: Configure Ethernet interfaces of PC1, PC2, and PC3.

## Step 4: Test the PC configuration by pinging the default gateway from the PC.

# Task 4: Configure OSPF on the R1 Router

## Step 1:	Use the router ospf command in global configuration mode to enable OSPF on the R1 router
- R1(config)#router ospf 1

# Step 2: Configure the network statement for the LAN network.
- R1(config-router)#network 172.16.1.16 0.0.0.15 area 0
- R1(config-router)# network 192.168.10.0 0.0.0.3 area 0
- R1(config-router)# network 192.168.10.4 0.0.0.3 area 0
- R1(config-router)#end

# Task 5: Configure OSPF on the R2 and R3 Routers

# Task 6: Configure OSPF Router IDs

## Step 1:	Examine the current router IDs in the topology.
- R3#show ip protocols
- R3#show ip ospf
- R3#show ip ospf interface

## Step 2: Use loopback addresses to change the router IDs of the routers in the topology. 
- R1(config)#interface loopback 0 
- R1(config-if)#ip address 10.1.1.1 255.255.255.255
- R2(config)#interface loopback 0
- R2(config-if)#ip address 10.2.2.2 255.255.255.255

- R3(config)#interface loopback 0
- R3(config-if)#ip address 10.3.3.3 255.255.255.255

## Step 3: Reload the routers to force the new Router IDs to be used. 

## Step 4: Use the show ip ospf neighbors command to verify that the router IDs have changed.
- R1#show ip ospf neighbor
- R2#show ip ospf neighbor
- R3#show ip ospf neighbor

## Step 5:	Use the router-id command to change the router ID on the R1 router.
- R1(config)#router ospf 1
- R1(config-router)#router-id 10.4.4.4
- R1#(config-router)#end
- R1# clear ip ospf process 
Reset ALL OSPF processes? [no]:yes

## Step 6: Use the show ip ospf neighbor command on router R2 to verify that the router ID of R1 has been changed.

## Step 7:	Remove the configured router ID with the no form of the router-id command.
- R1(config)#router ospf 1
- R1(config-router)#no router-id 10.4.4.4

## Step 8:	Restart the OSPF process using the clear ip ospf process command.
- R1(config-router)#end
- R1# clear ip ospf process 
Reset ALL OSPF processes? [no]:yes



 
