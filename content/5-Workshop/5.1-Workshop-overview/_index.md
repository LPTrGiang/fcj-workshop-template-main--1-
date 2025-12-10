---
title: "Introduction"
date: "`r Sys.Date()`"
weight: 1
chapter: false
pre: " <b> 5.1. </b> "
---

#### VPC endpoints
+ **VPC endpoints** are virtual devices that are horizontally scalable, redundant, and highly available. They enable your VPC resources to communicate with AWS services without introducing additional availability risks.
+ Compute resources running inside a VPC can access **Amazon S3** using a **Gateway endpoint**. **PrivateLink interface endpoints** can also be used by compute resources running in a VPC or in on-premises environments.

#### Workshop overview
In this workshop, you will work with two VPCs:
+ **"VPC Cloud"**: This VPC hosts cloud-based resources such as a **Gateway endpoint** and an EC2 instance for testing.
+ **"VPC On-Prem"**: This VPC simulates an on-premises environment, such as a factory floor or corporate datacenter. An EC2 instance running strongSwan VPN software has been deployed and automatically configured to establish a Site-to-Site VPN tunnel with AWS Transit Gateway. This VPN connection simulates on-premises connectivity to AWS.  
  To minimize workshop costs, only a single VPN instance is provided. For production workloads, AWS recommends deploying multiple VPN devices to achieve high availability.
