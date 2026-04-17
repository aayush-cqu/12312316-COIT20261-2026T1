# Week 05: Switching and VLAN
## Task 1: Setup VLANs on Switch


## Testing Results

### Task 1: Setup VLANs on Switch

- Successfully created a topology with four Linux Hosts and one OpenvSwitch.
  
- Assigned all hosts IP addresses in the same subnet.
  
- Verified that all hosts could communicate before VLAN configuration.
  
- Checked switch port details using:

              ovs-vsctl show
  
## Outputs

1. GNS3 project \
[Vlan-basics](GNS3_files/Vlan-basics-12312316.gns3project)


2. Screenshot of Network \
![Network-Screenshot](images/Vlan-basics(12312316)-network.png)



2. Screenshot of Ports and Tags \
![PortsandTags-Screenshot](images/Vlan-basics(12312316)-ports.png) 



## Task 2: Setup VLANs on a Router

## Testing Results

  Added a Linux Router connected to switch port eth0.
  
  Configured two host groups into different IP subnets.
  
  Configured switch trunk port to carry multiple VLANs:
  
                ovs-vsctl set port eth0 trunks=[]
                
  Created router VLAN sub-interfaces:
  
                ip link add link eth0 name eth0.10 type vlan id 10
                ip link add link eth0 name eth0.20 type vlan id 20
                
  Assigned IP addresses to router sub-interfaces.
  
  Verified that all hosts could communicate across VLANs through the router.
  
## Outputs

1. GNS3 project \
[Vlan-Router](GNS3_files/Vlan-Router-12312316.gns3project)


2. Screenshot of Network \
![Network-Screenshot](images/Vlan-Router(12312316)-Router.png)



2. Screenshot of Ports and Tags \
![PortsandTags-Screenshot](images/Vlan-basics(12312316)-ports.png)




## Reflections

This week helped me understand how VLANs improve network organisation and security by separating devices into different broadcast domains. I observed that devices in different VLANs could not communicate without routing. Configuring a router-on-a-stick setup showed how one physical router interface can support multiple VLANs using sub-interfaces. This practical activity improved my understanding of switch management, VLAN tagging, and inter-VLAN routing.

## Notes on Key Concepts Learned

### VLAN

  A VLAN (Virtual Local Area Network) logically separates devices on the same physical switch into different networks.

### Access Port

  An access port connects end devices such as PCs and belongs to one VLAN only. Frames are sent untagged to the host.

### Trunk Port

  A trunk port carries traffic for multiple VLANs between switches or between a switch and router using VLAN tags.

### OpenvSwitch

  OpenvSwitch is a virtual managed switch used in GNS3 that supports VLANs and advanced switching features.



## Learnings

How to configure VLANs on switch access ports

Difference between access ports and trunk ports

How VLANs isolate network traffic

How to verify switch configuration

How to create VLAN sub-interfaces on a router

Practical use of OpenvSwitch commands in GNS3


