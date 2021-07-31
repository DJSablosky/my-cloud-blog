---
title: "Amazon WorkSpaces"
date: 2021-07-26T13:55:21-04:00
draft: false

categories: [Computing]
tags: [WorkSpaces]
toc: false
author: "Daniel Sablosky"
---
Amazon WorkSpaces is a managed desktop as a service product available within Amazon Web Services (AWS) like Citrix or Remote Desktop Services.  Users are provided dedicated virtual Linux or Windows desktops of various sizes, memory, and features.  Applications and their state are maintained whether users log on or off from different locations.  AWS or custom images can provide commercial applications that can be utilized on the Amazon WorkSpaces, such as the Workspaces Graphics Bundle recommended for ArcGIS Pro.  Amazon WorkSpaces are charged on a monthly or hourly basis; hourly basis allows the suspension of an Amazon WorkSpace when not in use but still incurs a minimum monthly cost for infrastructure.  

Amazon WorkSpaces requires the AWS Directory Service as an identity store for authentication. AWS Directory Services includes AWS Managed Microsoft Active Directory (AD), AD Connector, and Simple AD.  A trust relationship can also be established between an AWS Managed Microsoft AD and a domain on premises.  Windows bundles can access Amazon FSx for Windows File Servers as well as Windows resources on Amazon Elastic Compute Cloud (EC2) instances or on premises via AWS Virtual Private Networks (VPN) or AWS Direct Connect private virtual interfaces.  AWS Direct Connect public virtual interfaces can also be used by the client for improved throughput and lower latency.   Amazon WorkSpaces include a system volume and a user volume that can be encrypted at rest by Amazon Key Management Service (KMS).

Amazon WorkSpaces are accessed using client software installed on a supported desktop, laptop, or tablet.   Each Amazon WorkSpace uses an elastic network interface (ENI) injected into an Amazon Virtual Private Cloud (VPC).  Shared streaming gateways act as endpoints for the Amazon WorkSpaces client application and use AWS Directory Service for authentication.  These gateways communicate with Amazon WorkSpaces in an Amazon VPC for any management traffic.  Amazon VPC infrastructure is used for internal Amazon VPC traffic, public Internet access, or access to networks on premises, and charged accordingly.  Amazon WorkSpaces occupy a subnet in a single Availability Zone and are not highly available by design.

Amazon WorkSpaces is FedRAMP High Compliant, and a connection health check to commercially available regions is provided at:

[Amazon WorkSpaces](https://clients.amazonworkspaces.com/Health.html)