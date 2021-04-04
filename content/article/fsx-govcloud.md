---
title: "Amazon FSx for Windows File Server in AWS GovCloud"
date: 2021-04-04T18:31:12-04:00
draft: false

categories: [Storage]
tags: [FSx]
toc: false
author: "Daniel Sablosky"
---
Amazon Web Services (AWS) shares responsibility for security and compliance by protecting 
the infrastructure of its services while customers configure security for their selected 
services.  In December, 2020, Amazon FSx for Windows File Server became available in the AWS GovCloud (US) Regions as a shared file system for Windows environments (as opposed to Amazon Elastic File System, which is generally used more for Linux systems.)  Amazon FSx for Windows File Server provides fully managed native Windows file shares designed for Windows integration, including Active Directory running on AWS or on-premises.  Amazon FSx is a resilient and highly available system that can be deployed in a single Availability Zone (AZ) or Multi-AZ.  

File systems created within Amazon FSx are accessible within a Virtual Private Cloud (VPC), over VPC peering connections, over Virtual Private Network (VPN) connections, or over Direct Connect (DX).  Amazon FSx is accessible over Service Message Block (SMB) protocol, which operates in the application layer (Layer 7) of the Open Systems Connection (OSI) model and creates connections between servers and clients by sending multiple request-response messages back and forth.  SMB is not as fast as File Transfer Protocol (FTP) but it provides more features for directory structure, network drive mapping, and encryption.  SMB is utilized in Windows Server, Hyper-V, and Microsoft SQL Server.

In order to assess Amazon FSx for Windows File Server in AWS GovCloud (US), I completed the 
workshop:

[Windows File Storage the AWSome Way!](https://github.com/aws-samples/amazon-fsx-tutorial/tree/master/windows-file-server)

The workshop predates its availability in GovCloud, but I was able to make some minor 
adjustments to the AWS CloudFormation script provided in order to test in AWS GovCloud (US) as well as create a hard disk drive (HDD) Multi-AZ file system in the console.  Amazon FSx offers the choice of HDD or solid state drives (SSD) for storage.  SSD is data stored in integrated circuits, and HDD stores data magnetically on spinning disks.  While HDD is considered more of a legacy, it is more cost effective for general workloads like home directories, departmental shares, and content management systems.  SSD offers better performance and latency for databases, media processing workloads, and data analytics applications. 

Amazon FSx for Windows File Server provides an endpoint in the console to manage file shares remotely.  Remote PowerShell sessions can be used to create a data duplication optimization schedule, enable shadow copies for the entire file system, and manage user storage quotas.  Data deduplication is a background process that stores duplicated portions of a dataset only once, eliminating redundant data and reducing storage costs.  Shadow copies are snapshots of file systems or volumes that can be created while they are in use in Windows.  Remote PowerShell sessions can also be used to create a Continuous Access (CA) share for High Availability (HA) Microsoft SQL Server active database files when SQL Server is deployed across multiple database nodes in a Windows Server Failover Cluster (WSFC).

Performance testing can be performed on Amazon FSx file systems using DiskSpd or **fio**, and Amazon CloudWatch alarms and Amazon Simple Notification Service (SNS) are fulling integrated with Amazon FSx.

Should Amazon FSx become FedRAMP compliant, it will be listed at:

[AWS Services in Scope by Compliance Program](https://aws.amazon.com/compliance/services-in-scope/)