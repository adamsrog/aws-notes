# Virtual Private Cloud 

AWS re:Invent 2015 | (NET201) VPC Fundamentals and Connectivity Options - https://www.youtube.com/watch?v=5_bQ6Dgk6k8

## Choosing an IP Address range for VPC
* CIDR Notation (Classless internet domain routing)
* Use an RFC 1918 range
* Use /16 (CIDR), allows for 64,000 IP addresses
* Avoid overlapping with other networks you may connect to

## Set up subnets
* Use a subnet for each availablity zone
* /24 gets you 251 IP addresses, not 256 because Amazon reserves the first 5.
* eu-west-1a = 172.31.0.0/24
* eu-west-1b = 172.31.1.0/24
* eu-west-1c = 172.31.2.0/24 ...etc

## Create a route to the Internet
* Route table contains rules for which packets go where
* Create an Internet gateway to allow it to send packets outside the VPC
* 0.0.0.0/0 igw-######

## Network ACLs
* Stateless firewall rules
* Apply specific rules to specific subnets

## Security Groups
* Group each type of EC2 instance into security groups (i.e. webservers, databases, etc)
* Webservers would allow traffic from anywhere (0.0.0.0/0)
* Databases would only speak to the webservers - they're the "only ones who have any business talking to it"
  * Allow TCP traffic on port XXXX from another security group (the webservers)
  * Best practice: specify traffic by security groups.
* Security group: who can reach me
* IAM roles: what I can do

## NAT access to Internet
* Use NAT to allow non-internet facing instances to access patches/updates.
* No need to give them a public IP address.
* Amazon NAT instance image: amzn-ami-vpc-nat

## VPC Peering
* Connecting a VPC to other VPCs
* Can't peer IP ranges that overlap
* Allows private connectivity between VPCs
* Request/accept a peer request, then create routes that allows communication between the two ranges.

## Extend your own network into the VPC
* VPN or Direct Connect. Allows the two networks to talk to eachother.
* VPN is a pair of IPSec tunnles over the Internet.
* Direct Connect is a dedicated line with lower per-GB data transfer rates.

## DNS in a VPC
* DNS resolution - do you want Amazon to do DNS for you?
* DNS hostnames - do you want to Amazon to set up hostnames for EC2 instances?
* Route 53 private hosted zones allow for DNS within your private VPC

## VPC Flow Logs
* See all your traffic by dumping all logs so you can troubleshoot/analyze traffic
