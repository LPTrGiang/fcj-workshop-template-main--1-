---
title : "Prepare the environment"
date : "`r Sys.Date()`"
weight : 1
chapter : false
pre : " <b> 5.4.1 </b> "
---

To prepare for this part of the workshop, you will need to:
+ Deploy a CloudFormation stack
+ Modify a VPC route table

These components work together to simulate on-premises DNS forwarding and name resolution.

---

#### Deploy the CloudFormation stack

The CloudFormation template creates additional services required to simulate an on-premises environment:

+ A Route 53 Private Hosted Zone that hosts Alias records for the PrivateLink S3 endpoint  
+ A Route 53 **Inbound Resolver endpoint** that allows **VPC Cloud** to resolve inbound DNS queries to the Private Hosted Zone  
+ A Route 53 **Outbound Resolver endpoint** that allows **VPC On-prem** to forward DNS queries for S3 to **VPC Cloud**
![route 53 diagram](/images/5-Workshop/5.4-S3-onprem/route53.png)

1. Click the following link to open the [AWS CloudFormation console](https://us-east-1.console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/quickcreate?templateURL=https://s3.amazonaws.com/reinvent-endpoints-builders-session/R53CF.yaml&stackName=PLOnpremSetup). The required template will be pre-loaded into the menu. Accept all default and click Create stack.

![Create stack](/images/5-Workshop/5.4-S3-onprem/create-stack.png)

![Button](/images/5-Workshop/5.4-S3-onprem/create-stack-button.png)

It may take a few minutes for stack deployment to complete. You can continue with the next step without waiting for the deployemnt to finish.

#### Update on-premise private route table

The stack may take several minutes to deploy. You may proceed to the next step without waiting for completion.

---

#### Update the on-premises private route table

This workshop uses a **strongSwan VPN** running on an EC2 instance to simulate connectivity between an on-premises datacenter and the AWS Cloud.  
Most components are pre-provisioned, but to finalize the configuration you must update the **VPC On-prem** route table so that traffic destined for the cloud is routed through the strongSwan VPN instance.

1. Open the **Amazon EC2 console**.

2. Select the instance named **infra-vpngw-test**.  
   On the *Details* tab, copy the **Instance ID** and paste it into a text editor for later reference.


![ec2 id](/images/5-Workshop/5.4-S3-onprem/ec2-onprem-id.png)

3. Navigate to the VPC menu by using the Search box at the top of the browser window.

4. Click on Route Tables, select the RT Private On-prem route table, select the Routes tab, and click Edit Routes.

![rt](/images/5-Workshop/5.4-S3-onprem/rt.png)

5. Click Add route.
+ Destination: your Cloud VPC cidr range
+ Target: ID of your infra-vpngw-test instance (you saved in your editor at step 1)

![add route](/images/5-Workshop/5.4-S3-onprem/add-route.png)

6. Click Save changes



