---
title: "Amazon EKS in AWS GovCloud"
date: 2021-04-28T11:27:20-04:00
draft: false

categories: [Containers]
tags: [EKS]
toc: false
author: "Daniel Sablosky"
---
Instead of a monolithic application, many modern applications can be composed of several independent stateless microservices, each performing a particular function and running in a container.  This improves disaster recovery and continuous deployment.  Containers are light-weight units with the necessary components that software needs to run in a virtual operating environment.  Docker containers are open source and often used with Linux workloads, but Windows containers are also available. 

Docker containers includes code, libraries, virtual kernel, and everything the microservices need to run.  The Docker container runs on a Docker host, which is the runtime environment for the container.  The Docker host in turn runs on a physical server or a virtual server.  As the application grows, it can be scaled by simply adding more Docker containers. 

Kubernetes (K8s) is an open-source tool originally created by Google that deploys, manages, and maintains Docker containers using a central control plane.  A K8s cluster consists of a control plane and a set of worker nodes.  The control plane manages configuration, schedules the deployment of containers on worker nodes, and conducts auto scaling.  The worker nodes provide the Docker container runtime environments as well as the containers that compose the application.  K8s supports a declarative model in which K8s objects use configuration files to maintain a desired state. 

Amazon Elastic Kubernetes Service (EKS) is a managed service that runs the K8s control planes and worker nodes on Amazon Web Services (AWS).  Amazon EKS is certified K8s conformant, and it allows K8s clusters to be provisioned and scaled across multiple AWS Availability Zones (Multi-AZ).  Amazon EKS can automatically detect and replace unhealthy worker nodes as well as handle all the security patching and updates for the control plane.  It can manage K8s clusters on Amazon Elastic Compute Cloud (EC2) instances optimized for Amazon EKS, enhancing high availability and fault tolerance for stateful, long running applications.  Serverless containers can also be run on AWS Fargate with Amazon EKS, which alleviates the management of worker nodes and is more cost effective.  AWS Fargate is best for stateless processes, but it is not ideal for applications with persistence volumes or file systems.   

Amazon EKS is deeply integrated with AWS, including AWS CloudTrail, Amazon CloudWatch, AWS Identity & Access Management (IAM), Amazon Virtual Private Cloud (VPC), Auto Scaling Groups, and Elastic Load Balancing.  The control plane is a fully managed service that runs across three AZs in a single region, and the latest security patches are automatically applied.  The control plane infrastructure is not shared with any other Amazon EKS cluster or AWS account. 

Amazon EKS is available in the AWS GovCloud (US) Regions and compliant with the Federal Risk and Authorization Management Program (FedRAMP). 