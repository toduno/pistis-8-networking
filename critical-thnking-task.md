# NETWORKING CRITICAL THINKING TASK: SUBNETTING

## SUBNETTING IP ADDRESS FOR ELDORA BOTTLING COMPANY

### Requirements

- Departments or areas needing separate subnets.
  
**_HR/Personnel department and IT/Administrative department._**

- Plan for future growth.

**_The HR department needs 30 ip addresses and additional 30 for future use. IT needs 60 ip addresses and additional 60 for future use._**

### Address Allocation

**_Eldora’s IP address range or space is 192.168.0.0, subnet mask 255.255.255.0 or /24(CIDR) (or class C) i.e. 32-bits (ipv4), with 256 available addresses (i.e. 2 ^ 8) within the range of 192.168.0.0 to 192.168.0.255 which will be further broken down into smaller subnets below to allocate subnets and ip addresses to departments._**

1. Understand usable host addresses.
  
- **_Usable host addresses for each subnet is every other address except the IP addresses needed for the network identity itself which are the first IP and last IP (broadcast address) derived by the formula (2^x)-2, where x is the number of hosts derived from the bits left after identifying subnets e.g. in a 32-bit subnet mask i.e class C where 8-bits are left for host._**

- **_For the HR department: if 3-bits are used to identify subnets, 5-bits are left for the host, and so a subnet will be 2^5-2=30 usable host addresses._**

- **_For the IT department: if 2-bits are used to identify subnets, 6-bits are left for the host, and so a subnet will be 2^6-2=62 usable host addresses._**

2. Choose subnet sizes based on needs.

- **_HR department - needs 30 ip addresses in total, subnet the 192.168.0.0/24 range further with 3 bits borrowed to make /27(CIDR) which gives 8 subnets (2 ^ 3) with 32 addresses each (256/8=32, or 32-27=5 and 2^5=32) making 30 usable addresses (if you remove the first and last IP) and 2 subnets taken, 1 for current need and the other for future use. E.g. (with full 32 ip addresses) subnet 1 = 192.168.0.0/27, subnet 2 = 192.168.0.32/27._**
  
- **_IT department - needs 64 ip addresses in total, we create another set of subnets by borrowing 2 more bits to make /26(CIDR) which gives 4 subnets (2 ^ 2) with 64 addresses each (256/4=64, or 32-26=6 and 2^6=64) making 62 usable addresses (if you remove the first and last IP) and 2 subnets taken, 1 for current need and the other for future use. E.g. (with full 64 ip addresses) subnet 1 = 192.168.0.64/26, subnet 2 = 192.168.0.128/26._**

### Subnet Masks

1. Learn how subnet masks work.

- **_Subnet masks specify which portions of the subnet are the network and which portions are the host. The company IP address has a /24 CIDR subnet mask (32-bits) or class C that separates the host from the network and has 8 bits for the host and the rest for the network according to how class C works for small businesses perfect for this company. This was further subnetted into /27 and /26 subnet masks by lending out 2 and 3 bits respectively from the 8 bits to cater for the needs of the HR and IT departments seeking 30 IP addresses and 60 IP addresses respectively._**

2. Match subnet masks to subnet sizes.

- **_/27 subnet mask was used to allocate 2 subnets to the HR department needing 30 host ip addresses and each to the subnets. /26 subnet mask allocated 2 subnets to the IT department needing 60 host ip addresses and to each subnets._**

### Documentation

1. Create a clear plan with IP ranges and subnet masks.

- **_Using a /24 subnet mask of network address 192.168.0.0, I subnetted it and created 2 more subnet masks for our departments in /27 and /26 for HR and IT respectively by borrowing bits from /24. HR will have 30 IP addresses and 2 subnets and its usable IP ranges from /27 subnet mask (32-2=30 IP per subnet) is 192.168.0.1 to 192.168.0.63 : subnet 1 = 192.168.0.1/27, subnet 2 = 192.168.0.33/27. Subnet 1 30 ip addresses available for use are - 192.168.0.1 to 192.168.0.30._**
  
- **_IT will have 60 IP addresses and 2 subnets and its usable IP ranges from /26 subnet mask (64-2=62 IP per subnet) is 192.168.0.65 to 192.168.0.191: subnet 1 = 192.168.32.65/26, subnet 2 = 192.168.0.129/26. Subnet 1 62 usable ip addresses are - 192.168.0.65 to 192.168.0.126._**

### Troubleshooting

1. Prepare for scenarios with communication issues.

- **_Communications issues that can occur in this setup is IP overlap. If HR and IT departments have the same IP range, for instance, a 192.168.0.192 subnet, and HR wants to route traffic to the same subnet in the IT department, the router of HR will loop packet back into the HR department._**

2. Handle IP conflicts and routing challenges.

- **_IP conflict and routing challenges were handled by: Ensuring I don’t have overlapping subnets by using different IP spaces/subnets._**

### Future Growth

1. Allow for expansion in your plan.

- **_Since 2 subnets with 30 IP addresses each were created for the HR department and only 1 subnet used, the other 1 subnet with 30 IP addresses is available for future growth. Also, the IT department has 2 subnets with 62 usable IP addresses each with only 1 subnet occupied and the other available for future growth._**

2. Modify as needed for new devices or departments.

- **_IP addresses can be allocated to other departments by borrowing the remaining bits left in this case 3-bits from the /24 CIDR 8-bits (since 5 has been used for subnetting) to create a new subnet (super-subnet(s) and/or subnets as done for the HR and IT departments) and host IP addresses._**

### Optimization

1. Explore efficient routing and reduced broadcast traffic.

- **_To reduce broadcast traffic, I avoided using IP addresses specially meant for broadcasting. This way broadcast traffic will not interfere with the traffic in the subnets in the departments i.e. HR and IT departments._**

2. Optimize IP address use with DHCP and reservations.

- **_To optimize IP address use, I used Dynamic Host Configuration Protocol (DHCP) with reservations. DHCP is a protocol that automatically assigns IP addresses to devices on a network based on its MAC address avoiding the need to manually configure IP addresses for each device on the network. DHCP reservations allow you to assign a specific IP address to a device based on its MAC address. This ensures that the device always receives the same IP address, which can be useful for devices that require a static IP address. For instance, some devices on Eldora’s network, which are used by other users and services (servers, printers, scanners, routers, switches, storage devices, etc.), require a fixed static IP that should not change._**

**_Two ways to assign a specific IP address to a device on a TCP/IP network are to:_**

1. **_Manually set a static IP address in the device settings_**

2. **_Reserve an IP address for the device on the DHCP server._**

**_The centralized reservation of IP addresses on the DHCP Server allows you to manage the IP addresses of the devices on your network from a single console. There is also no need to log on to each device locally and manually set the IP parameters for the network adapter. So, I added a DHCP reservation on Windows server via DHCP Server role to assign dynamic IP addresses to client devices._**
