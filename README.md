# AWS Cloud Formation (Infrastructure as Code) 

## Overview

This is a simple AWS deployment that consists of the following resources:

- 1 VPC
- 2 Public Subnets across 2 Availability Zones (AZs)
- 2 Private Subnets across 2 AZs
- 1 Internet Gateway
- 1 NAT Gateway
- 1 S3 Bucket for static web hosting
- 1 Load Balancer
- 2 Web Server EC2 instances (Private Subnets)
- 1 Bastion Host EC2 instance (Public Subnet)
- A few ACLs, Security Groups, and routes.

## Important Note

I couldn't figure out why attaching the NAT Gateway is never marked as complete, so when launching the stack make you **Preserve** the resources in case of failure. Although this is not marked as complete by Cloud Formation, it is being normally deployed. 

## To be done
- Fix the problem with the incomplete NAT Gateway attachment 
- This deployment would benefit from additional security, identity, and compliance resources. Additionally, splitting the stack into different files, such as one for EC2 instances and another for network resources, would be recommended. This could be achieved by using "Exports," but the intent of this project is to keep it all in one file for simplicity.


