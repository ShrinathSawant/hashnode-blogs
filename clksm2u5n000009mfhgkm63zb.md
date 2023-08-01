---
title: "Exploring VPC: An In-depth Look at Its Key Components"
datePublished: Tue Aug 01 2023 18:07:09 GMT+0000 (Coordinated Universal Time)
cuid: clksm2u5n000009mfhgkm63zb
slug: exploring-vpc-an-in-depth-look-at-its-key-components
tags: aws, cloud-computing, devops, vpc, aws-vpc

---

### VPC: Virtual Private Cloud:

VPC is a logically isolated network environment you can create in the cloud.

You have complete control over your virtual networking environment. With Amazon VPC, you can:

• Select your IP address range.

• Create subnets.

• Configure route tables and network gateways.

You can use both IPv4 and IPv6 in your VPC for secure and easy access to resources and applications.

* You can have multiple VPCs in an AWS region (max. 5 per region – soft limit)
    
* Max. CIDR per VPC is 5, for each CIDR:
    
    • Min. size is /28 (16 IP addresses)
    
    • Max. size is /16 (65536 IP addresses)
    
* Because VPC is private, only the Private IPv4 ranges are allowed:
    
    • 10.0.0.0 – 10.255.255.255 (10.0.0.0/8)
    
    • 172.16.0.0 – 172.31.255.255 (172.16.0.0/12)
    
    • 192.168.0.0 – 192.168.255.255 (192.168.0.0/16)
    

### Subnet:

A subnet is a range of IP addresses in your VPC. You can launch AWS resources, such as EC2 instances, into your subnets. Each subnet resides entirely within one Availability Zone.

There could be two categories of subnets, i.e. Public subnet and Private subnet.

Use a public subnet for resources that must be connected to the internet and a private subnet for resources that won't be connected to the Internet directly.

The first four IP addresses and the last IP address in each subnet CIDR block are reserved and cannot be assigned to an instance.

For example, in a subnet with CIDR block 10.0.0.0/24, the following five IP addresses are reserved:

• 10.0.0.0: Network address.

• 10.0.0.1: Reserved by AWS for the VPC router.

• 10.0.0.2: Reserved by AWS. The IP address of the DNS server is always the base of the VPC network range plus 2.

• 10.0.0.3: Reserved by AWS for future use.

• 10.0.0.255: Network broadcast address. AWS does not support broadcast in a VPC; therefore, we reserve this address.

### Internet Gateway (IGW):

IGW allows communication between the resources inside VPC and the internet with the help of a route table. It scales horizontally and is highly available and redundant. One VPC can only be attached to one IGW and vice versa

An internet gateway serves two purposes:

1. It provides a target in your route table for internet-routable traffic.
    
2. It protects IP addresses on your network by performing NAT.
    

**Provides a target in your route table for internet-routable traffic**

A subnet does not allow outbound traffic by default. Your VPC uses route tables to determine where to route traffic. To allow your VPC to route internet traffic, you create an outbound route in your route table with an internet gateway as a target, or destination.

**Protects IP addresses on your network by performing NAT**

Resources on your network that connect to the internet should use two kinds of IP addresses:

• Private IP: Use private IPs for communication within your private network. These addresses are not reachable over the Internet.

• Public IP: Use public IP addresses for communication between resources in your VPC and the internet. A public IP address is reachable over the internet.

### Route Table:

A route table contains a set of rules (routes) that the VPC uses to determine where to direct network traffic.

When you create a VPC, it automatically has a main route table. Initially, the main route table contains only a single route. This local route permits communication for all the resources within the VPC. You can't modify the local route in a route table. You can create additional custom route tables for your VPC.

Each subnet in your VPC must be associated with a route table. If you don't explicitly associate a subnet with a particular route table, the subnet is implicitly associated with and uses the main route table.

A subnet can be associated with only one route table at a time, but you can associate multiple subnets with the same route table.

### NAT Gateway (Network Address Translation):

NAT Gateway can be used to allow private IP networks to connect to the internet. In other words, it acts as an agent between the Internet (public network) and a local network (private network).

They are horizontally scaled, redundant, and highly available within a single availability zone.

Must create multiple NAT Gateways in multiple AZs for fault tolerance.

NAT gateways provide a target in your subnet route tables for internet-routable traffic.

• Instances in the private subnet can initiate outbound traffic to the internet or other AWS services.

• NAT gateway prevents private instances from receiving inbound traffic from the internet.

### NACL:

NACLs are an additional layer of security that operates at the subnet level. They act as stateless traffic filters for inbound and outbound traffic at the subnet boundary.

Unlike Security Groups, NACLs are associated with subnets, and each subnet can have only one NACL. However, multiple subnets can share the same NACL.

NACLs consist of a numbered list of rules (numbered in ascending order) that are evaluated in order from lowest to highest.

Each rule in the NACL includes a rule number, protocol, rule action (allow or deny), source or destination IP address range, port range, and ICMP (Internet Control Message Protocol) type.

NACL rules can be configured to allow or deny specific types of traffic based on the defined criteria.

They are stateless, which means that if an inbound rule allows traffic, the corresponding outbound traffic must be explicitly allowed using a separate outbound rule.

Changes made to NACL rules may take some time to propagate to all the resources using the associated subnet.

### Security Groups:

Security Groups act as virtual firewalls for Amazon EC2 instances (virtual servers) at the instance level. They control inbound and outbound traffic by allowing or denying specific protocols, ports, and IP addresses.

Inbound rules determine the traffic that is allowed to reach the EC2 instance, whereas outbound rules control the traffic leaving the instance.

Security Groups can be configured using IP addresses, CIDR blocks, security group IDs, or DNS names to specify the source or destination of the traffic.

They operate at the instance level and evaluate the rules before allowing traffic to reach the instance. Security Groups are stateful, meaning that if an inbound rule allows traffic, the corresponding outbound traffic is automatically allowed, and vice versa.

Changes made to security group rules take effect immediately.

### Comparing security groups and network ACLs

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690911290446/5c7e0968-befc-4b52-a94c-8a19f9a669ca.png align="center")

A security group acts as a firewall for associated EC2 instances, controlling both inbound and outbound traffic at the instance level. Network ACLs act as a firewall for associated subnets, controlling both inbound and outbound traffic at the subnet level.

Both can have different default configurations depending on how they are created. Security groups

• Security groups in default VPCs allow all traffic.

• New security groups have no inbound rules and allow outbound traffic.

Network ACLs

• Network ACLs in default VPCs allow all inbound and outbound IPv4 traffic.

• Custom network ACLs deny all inbound and outbound traffic until you add rules.