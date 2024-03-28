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

### Bucket

Deploys a bucket for static web hosting, you will still need to upload the html file.
More information can be found [here](https://docs.aws.amazon.com/AmazonS3/latest/userguide/WebsiteHosting.html). 

### Netork

Deploys a VPC with subnets (private/public) across 2 different availability zones, ensuring high availability to our web servers.
More information can be found [here](https://docs.aws.amazon.com/whitepapers/latest/real-time-communication-on-aws/use-multiple-availability-zones.html).

### Instances

Deploys a Bastion host to allow users to ssh into the webservers. Bastion host is located in one of the public subnets, and can access services on both AZs.
More information about bastion hosts [here](https://www.knowledgehut.com/tutorials/aws/aws-bastion-host).

Also deploys 2 web servers, one in each Private subnet. 

### Loadbalancer

Sets a target group (to both web-servers), and a listener on port 80. The loadbalancer spans across both AZs. This is good practice to distribute traffic across different instances, but also to ensure the service will continue to work if one instance fails.
More infor on load balancers [here](https://aws.amazon.com/elasticloadbalancing/).
