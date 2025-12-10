---
title : "Access S3 from VPC"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 5.3. </b> "
---

#### Using Gateway endpoint

In this section, you will set up a Gateway endpoint so that an EC2 instance can access Amazon S3 privately. By using the Gateway endpoint, all uploads to your S3 buckets stay within the AWS network and do not traverse the public internet.
To create the endpoint, you simply choose the target VPC and specify Amazon S3 as the service you want to connect to.

![overview](/images/5-Workshop/5.3-S3-vpc/diagram2.png)

#### Content

- [Create gateway endpoint](3.1-create-gwe/)
- [Test gateway endpoint](3.2-test-gwe/)