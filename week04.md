# Week 04: Routing

# Theory

## Routing Table
A routing table is a set of rules stored in a host or router that determines where IP packets should be sent. Each entry usually contains the destination network, next hop, and outgoing interface. Routing tables are essential for communication between different networks.


# Task 1: View Routing Tables  


# Testing Results

### Task 1: View Routing Tables
- Successfully created a topology with three Linux Hosts, one Linux Router, and one Ethernet switch.
- Configured two separate subnets with static IP addresses.
- Enabled IP forwarding on the router and disabled forwarding on all hosts.
- Verified forwarding status using:


                          sysctl net.ipv4.ip_forward=1

  
1. GNS3 Project file      
[GNS3 File](GNS3_files/View-Route-12312316.gns3project)   

2. Network Diagram   
![Screenshot](images/View_routes-12312316-network.png)

3. Record of IP Routes   
![IPRoutes-Screenshot](images/View_routes-12312316-Ipaddress-routingtable.png)   
  

4. Ping to other network       
![Ping-Screenshot](images/View_routes-12312316-ping.png)   

## Task 2: Dynamic Routing with OSPF

# Task 2: Dynamic Routing with OSPF

        Imported and ran the OSPF template project.
        
        Waited for all FRR routers to boot and accessed the frr# prompt.
        
        Verified OSPF neighbours using:
        
                        show ip ospf neighbor
                        
        Viewed OSPF learned routes using:
        
                        show ip ospf route
                        
        Viewed complete routing table using:
        
                        show ip route
                        
        Used traceroute to identify the path between two hosts.
        
        Disabled one link by stopping a NETem node.
        
        Ran traceroute again and confirmed traffic used a new path after OSPF recalculated routes.

        
## Outputs

1. GNS3 File demonstrating OSPF    
[GNS3-SPFile](GNS3_files/OSPF-Basics-12312316.gns3project)   

2. Network Diagram demonstrating OSPF     
![IPRoutes-Scr](images/OSPF-Basics-12312316-network.png)   

 

4. Routing table for two routers       
![OSPFTable-Screenshot](images/OSPF-12312316-routingtable-frr1.png)     
![OSPFTable-Screenshot](images/OSPF-12312316-routingtable-frr2.png)    

   

# OSPF Verification Commands and Routing Summary

# Routing Summary Table for All Routers

## 1. show ip ospf neighbor



## FRR-1
| Destination | Next Node |
|------------|-----------|
| 10.10.1.0/24 | Direct |
| 10.10.2.0/24 | Direct |
| 10.10.3.0/24 | Direct |
| 10.10.4.0/24 | FRR-2 |
| 10.10.5.0/24 | FRR-3 |
| 10.10.6.0/24 | FRR-2 |

## FRR-2
| Destination | Next Node |
|------------|-----------|
| 10.10.2.0/24 | Direct |
| 10.10.4.0/24 | Direct |
| 10.10.1.0/24 | FRR-1 |
| 10.10.3.0/24 | FRR-1 |
| 10.10.5.0/24 | FRR-4 |
| 10.10.6.0/24 | FRR-4 |

## FRR-3
| Destination | Next Node |
|------------|-----------|
| 10.10.3.0/24 | Direct |
| 10.10.5.0/24 | Direct |
| 10.10.1.0/24 | FRR-1 |
| 10.10.2.0/24 | FRR-1 |
| 10.10.4.0/24 | FRR-4 |
| 10.10.6.0/24 | FRR-4 |

## FRR-4
| Destination | Next Node |
|------------|-----------|
| 10.10.4.0/24 | Direct |
| 10.10.5.0/24 | Direct |
| 10.10.6.0/24 | Direct |
| 10.10.1.0/24 | FRR-2 |
| 10.10.2.0/24 | FRR-2 |
| 10.10.3.0/24 | FRR-3 |


6. Traceroute Command Output    
* Without stopping NETem 1     
![TracerouteScreenshot](images/FRR1-12312316-noterminating.png)   

* Stopping NETem 1     
![TracerouteScreenshot](images/FRR1-12312316-terminating.png)




## Reflections

This week gave me a deeper understanding of how routers make forwarding decisions using routing tables. I learned the importance of enabling IP forwarding so a Linux device can act as a router. The OSPF task was especially useful because it showed how dynamic routing protocols automatically adapt when network changes occur. Observing path changes with traceroute made the theory easier to understand in practice. I also became more confident working with FRR router commands in GNS3.

## Notes on Key Concepts Learned

### Routing Table

  A routing table contains routes that tell a device where to send packets based on the destination network.

### IP Forwarding

  IP forwarding allows a router to move packets between different interfaces and networks.

### Gateway

  A gateway is the router used by hosts to reach remote networks.


### OSPF

  OSPF (Open Shortest Path First) is a link-state routing protocol that selects the best path and recalculates routes when links fail.

### OSPF Neighbours

  Neighbour routers exchange routing information after forming adjacency.

### Traceroute

  Traceroute shows the hop-by-hop path packets take from source to destination.

### Network Redundancy

  Having multiple paths between networks improves reliability because traffic can use another path if one link fails.

### Learnings

    How to view and interpret routing tables
    
    How to configure and verify IP forwarding
    
    How OSPF discovers neighbours and learns routes
    
    How to analyse packet paths using traceroute
    
    How routing protocols recover from link failures
    
    Practical use of FRR router commands in GNS3

