---
title: Enable IPv6 on Oracle Cloud
date: 2021-8-24
categories: [oracle cloud, ipv6]
---

It is assumed that you have already created an instance.

1) Networking → Virtual Cloud Networks → \<network_name\> → CIDR Blocks/Prefixes → Add CIDR Block/IPv6 Prefix → Assign an Oracle allocated IPv6 /64 prefix → Add CIDR Blocks/Prefixes

2) Networking → Virtual Cloud Networks → \<network_name\> → Subnets → "..." right of the \<subnet_name\> → Edit → Assign an Oracle allocated IPv6 /64 prefix → enter any hexadecimal number between 00—FF (e.g. `7E`) → Save changes

3) Networking → Virtual Cloud Networks → \<network_name\> → Route Tables → Default Route Table for \<network_name\> → Add Route Rules  
Protocol Version: `IPv6`  
Target Type: `Internet Gateway`  
Destination CIDR Block: `::/0`  
Target Internet Gateway: `Internet Gateway <network_name>`

4) Networking → Virtual Cloud Networks → \<network_name\> → Security Lists → Default Security List for \<network_name\> → Egress Rules → Add Egress Rules  
Destination CIDR: `::/0`  
IP Protocol: `All Protocols`

5) Compute → Instances → \<instance_name\> → Attached VNICs → \<vnic_name\> → IPv6 Addresses → Assign IPv6 Address → Assign

# Testing
Just ping `google.com`. It will be done over IPv6. If not, try rebooting the machine.

# Port opening
[As for IPv4](https://medium.com/@fathi.ria/oracle-database-cloud-open-ports-on-oci-1af24f4eb9f2), but using `::/0` instead of `0.0.0.0/0` and `ip6tables` instead of `iptables`.
