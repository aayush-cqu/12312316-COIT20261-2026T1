# Week 02: Encapsulation and Decapsulation


# Theory

## Static IP Addressing
A static IP address is a manually assigned address that does not change automatically. It is useful in network labs because each host keeps the same address, making testing and troubleshooting easier. In this task, different Linux hosts were configured with static IP addresses using multiple methods.

## Methods of Assigning IP Addresses

### 1. Using GNS3 Configure Menu
The GNS3 Configure menu allows users to assign IP settings before starting the node. These settings are stored in the device configuration and are automatically applied when the node boots. This is the easiest method for beginners.

### 2. Using /etc/network/interfaces
The `/etc/network/interfaces` file is a Linux configuration file used to permanently assign network settings. By editing this file and restarting the interface with `ifdown` and `ifup`, the host can use a static IP address. This method is useful because the configuration remains after reboot.


## Task 1: Setting Static IP Addresses

## Testing Results
### Task 1: Setting Static IP Addresses
- Successfully created the project and connected four Linux Hosts to one Ethernet switch.
- Assigned static IP addresses to two hosts using the GNS3 Configure menu.
- Configured the third host by editing the `/etc/network/interfaces` file and reloading the interface using:


  
## Outputs


1. GNS3 File \
[GNS3-Setting IP](GNS3_files/Setting-IP-12312316.gns3project)

2. Network Diagram \
![Network-Screenshot](images/Setting-IP-12312316-network.png)

3. IP Address of Hosts 



**Host 1** \
![Host-Screenshot](images/Setting-IP-12312316-host1.png) 

**Host 2** \
![Host-Screenshot](images/Setting-IP-12312316-host2.png) 


**Host 3** 

The IP is assigned via console.



![Host-Screenshot](images/Setting-IP-12312316-host3.png) 

**Host 4** 

The IP for Host4 is assigned using command from console ( *ip address add <ipaddress>/<mask> dev eth0* ) \

![Host-Screenshot](images/Setting-IP-12312316-host4.png) 


## Task 2: Testing Network Connectivity and Delay with Ping

## Task 2: Testing Network Connectivity with Ping

Successfully pinged between hosts in the same LAN.

Received replies confirming connectivity between devices.

Observed RTT values in milliseconds.

Pinged an invalid IP address and observed 100% packet loss.

Tested options such as count, interval, and packet size.

## Outputs

1. Ping command output \
![Ping-Screenshot](images/Ping-Basics-12312316-simple.png)

2. Ping command and output to a wrong IP \
![Ping-Screenshot](images/Ping-Basics-12312316-error.png)

3. Ping command (and output) when limiting the count, setting the data size and interval to non-default values kept all together.

With all options \
![Ping-Screenshot](images/Ping-Basics-12312316-options.png)


## Reflections

This week improved my understanding of how IP addresses can be assigned in different ways on Linux systems. I learned that some methods are permanent, while others are temporary and useful for quick testing. Using ping helped me understand how devices communicate in a network and how to measure delay. It was also useful to see packet loss when sending traffic to a wrong address. These activities made me more confident using Linux networking commands in GNS3.

## Notes on Key Concepts Learned

# Static IP Address

  A static IP address is manually assigned and remains fixed unless changed by the user. It is commonly used in labs and servers.

# Permanent vs Temporary Configuration
  /etc/network/interfaces stores settings permanently.
  
  ip address add applies changes immediately but they are lost after reboot.
  
# Ethernet Switch

  A switch connects multiple devices in the same LAN and forwards frames based on MAC addresses.

# Ping

  Ping is a network utility that checks whether another device is reachable using ICMP messages.



# Ping Options

-c sets the number of packets sent.

-i changes the time interval between packets.

-s changes packet size.

# Learnings

How to configure static IP addresses using multiple methods

Difference between persistent and temporary settings

How to verify interface configuration

How to test connectivity between hosts

How ping options affect testing behaviour
