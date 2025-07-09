# AWS VPC Architecture Diagrams

---

## Diagram 1

![Diagram 1](png/diagram1.png)

The diagram shows a simple AWS architecture with the following components:

1. VPC (Virtual Private Cloud) - The outer blue container representing an isolated network environment in AWS.  
2. Public Subnet - A subnet within the VPC that has direct access to the internet.  
3. EC2 Instance - A virtual server (shown in orange) running within the public subnet.  
4. Route Table - Contains routing rules (172.16.0.0, 172.16.1.0, 172.16.2.0) that determine where network traffic is directed.  
5. Internet Gateway - The purple gateway icon on the left that allows communication between the VPC and the internet.

The arrows show the network flow:  
• The Internet Gateway connects to the Route Table  
• The Route Table connects to the EC2 Instance  

---

## Diagram 2

![Diagram 2](png/diagram2.png)

The diagram shows an AWS VPC architecture with public and private subnets:

1. VPC (Virtual Private Cloud) - The outer light blue container representing an isolated network environment in AWS.  
2. Public Subnet - Contains:  
   • Public Route Table (with routes 172.16.0.0, 172.16.1.0, 172.16.2.0)  
   • Public EC2 instance labeled as "Bastion Host" (orange server icon)  
3. Private Subnet - Contains:  
   • Private Route Table (with routes 172.16.0.0, 172.16.1.0, 172.16.2.0)  
   • Private EC2 instance (orange server icon)  
4. Internet Gateway - The purple gateway icon on the left that allows communication between the VPC and the internet.  
5. Connectivity:  
   • Internet Gateway connects to the Public Route Table  
   • Public Route Table connects to the Public EC2 instance  
   • Private Route Table connects to the Private EC2 instance  
   • Public EC2 connects to Private EC2 via SSH Access (shown by the arrow labeled "SSH Access")

This architecture follows a common security pattern where:  
• The public subnet has direct internet access through the Internet Gateway  
• The private subnet has no direct internet access  
• The public EC2 instance serves as a "jump box" or "bastion host" to access the private EC2 instance  
• The private EC2 instance is protected from direct internet exposure while still being accessible for management through the bastion host  

---

## Diagram 3

![Diagram 3](png/diagram3.png)

I've created a VPC architecture diagram that shows the setup you requested. The diagram illustrates:

1. A VPC (Virtual Private Cloud) containing:  
   • Two subnets: one public and one private  
   • Route tables for each subnet  
   • Network components for internet connectivity

2. The public subnet contains:  
   • A public EC2 instance that can directly access the internet  
   • A NAT Gateway that enables internet access for resources in the private subnet

3. The private subnet contains:  
   • A private EC2 instance that can only access the internet through the NAT Gateway

4. Networking components:  
   • Internet Gateway connected to the VPC for public internet access  
   • Public Route Table with routes (172.16.0.0, 172.16.1.0, 172.16.2.0)  
   • Private Route Table with routes (172.16.0.0, 172.16.1.0, 172.16.2.0)  
   • NAT Gateway in the public subnet providing outbound-only internet access for the private subnet

5. Traffic Flow:  
   • User connects to the Internet Gateway  
   • Traffic flows through the Public Route Table to the Public Subnet  
   • Public EC2 instance has direct internet access  
   • NAT Gateway in the Public Subnet provides outbound internet access for the Private Subnet  
   • Private Route Table directs traffic to the Private Subnet  
   • Private EC2 instance can only access the internet through the NAT Gateway
