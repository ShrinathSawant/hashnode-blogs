---
title: "Basics of IP Address and Classless Inter-Domain Routing (CIDR)"
datePublished: Mon Jul 31 2023 15:30:09 GMT+0000 (Coordinated Universal Time)
cuid: clkr112qj000209mk9yno5f8r
slug: basics-of-ip-address-and-classless-inter-domain-routing-cidr
tags: aws, cloud-computing, devops

---

# IP Address

An IP address includes information about the location of a resource within a network.

There are two IP address types:

## IPv4 addresses

IPv4 was developed in the early 1980s and uses 32-bit addresses.

The bits are grouped into four sets of 8 bits called octets.

Addresses in IPv4 are written by using numeric dot-decimal notation.

IPv4 addresses can create 4.3 billion addresses.

## IPv6 addresses

IPv6 was developed in 1998 to replace IPv4. IPv6 uses 128-bit addresses.

IPv6 addresses are eight groups of four hexadecimal digits, for a total of 16 octets.

The groups are written with a colon as a separator.

A full IPv6 address is often expressed in a shortened form. For example, 50b2:6400:0000:0000:0000:6c3a:b17d:0:10a9 can be written as 50b2:6400::6c3a:b17d:0:10a9.

The addresses have a capacity of 340 trillion trillion trillion addresses.

# Classless Inter-Domain Routing (CIDR)

CIDR is method to allocate the IP address range for network, subnet, etc.

A CIDR consists of two components:

### Base IP:

• Represents an IP contained in the range (XX.XX.XX.XX)

• Example: 10.0.0.0, 192.168.0.0, …

### Subnet Mask:

• Defines how many bits can change in the IP

• Example: /0, /24, /32

> Note: Max. CIDR per VPC is 5, for each CIDR:
> 
> • Min. size is /28 (16 IP addresses)
> 
> • Max. size is /16 (65536 IP addresses)
> 
> To calculate the subnet range use link: [Subnet range calculation](https://www.ipaddressguide.com/cidr)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1690816490553/06b5932d-f039-44a3-9a35-6a6c7e2690e0.png align="center")