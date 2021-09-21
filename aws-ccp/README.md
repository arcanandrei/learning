# Amazon Web Services - Certified Cloud Practitioner
## Table of Contents
 1. [Six advantages of Cloud Computing](#six-advantages-of-cloud-computing)
 2. [Types of Cloud Computing](#types-of-cloud-computing)
 3. [IAM - Identity Access Management](#iam---identity-access-management)
 4. [EC2 - Elastic Compute Cloud](#ec2---elastic-compute-cloud---infrastructure-as-a-service)
 5. [EC2 Instance Storage](#ec2-instance-storage)

# Six advantages of Cloud Computing
 1. Trade capital expense (**CAPEX**) for operational expense (**OPEX**)
 2. Benefit from massive economies at scale 
 3. Stop guessing capacity
 4. Increase speed and agility
 5. Stop spending money running and maintaining data centers
 6. Go global in minutes

# Types of Cloud Computing
 1. **Infrastructure as a Service (IaaS)**
    - Provide building blocks for IT
    - Provides networking, computers, data storage space
    - Highest level of flexibility
    - Easy parallel with traditional on-premises IT
 2. **Platform as a Service (PaaS)**
    - Removes the need for your organization to manage the underlying infrastructure
    - Focus on the deployment and management of your applications
 3. **Software as a Service (SaaS)**
    - Completed product that is run and managed by the service provider

## Notes

 - [x] On SaaS you **don't manage anything**
 - [x] On PaaS you **only** manage Applications and Data
 - [x] On IaaS you manage **Application, Data, Runtime, Middleware and OS**
 - [x] On-premise you manage **everything**

# IAM - Identity Access Management

Name | Description
-----|------------
**Users** | Mapped to a physical user, has a password for AWS Console
**Groups** | Contains users only
**Policies** | **JSON document** that outlines permissions for users or groups
**Roles** | For *EC2 (Elastic Compute Cloud)** instances or **AWS Services**
**Security** | **MFA** + **Password Policy**
**AWS CLI** | Manage your AWS services using the **command-line**
**AWS SDK** | Manage your AWS services using a **programming language**
**Access Keys** | Access AWS using the **CLI** or **SDK**
**Audit** | **Credential Reports** & **IAM Access Advisor**

# EC2 - Elastic Compute Cloud - Infrastructure as a Service

Name | Description
-----|------------
**EC2 Instance** | AMI (OS) + Instance Size (CPU + RAM) + Storage + Security Groups + EC2 User Data
**Security Groups** | Firewall attached to the EC2 Instance
**EC2 User Data** | Script launched at the first start of the instance
**SSH** | Start a terminal into our EC2 instances (port 22)
**EC2 Instance Role** | Link to IAM Roles
**Purchasing Options** | On-Demand, Spot, Reserved (Standard + Convertible + Scheduled), Dedicated Host, Dedicated Instance

## Notes
 - [x] To connect to your EC2 instance directly from your browser, use EC2 Instance Connect

## Purchasing Options Detailed
Option | Description | Max Discount
-------|-------------|-------------
**On-Demand Instances** | Short workload, predictable pricing | -
**Reserved** | Reserved instances for a period for exactly 1 year **or** 3 years | up to 72%
**Reserved Instances** | Ideal for long workloads | 1 year = +; 3 years = +++
**Convertible Reserved Instances** | Long workloads with flexible instances | up to 45%
**Scheduled Reserved Instances** | For example -- Every Thursday between 3PM and 6PM | -
**Spot Instances** | Short workloads, cheap and predictable to lose (less reliable) | up to 90%
**Dedicated Hosts** | Book an entire physical server, control instance placement | -
**Dedicated Instances** | No other customer will share your hardware | -

# EC2 Instance Storage

 1. **EBS Volumes (Elastic Block Store)**
    - Network drives attached to **one** EC2 instance at a time
    - Mapped to **an Availability Zone**
    - Can use EBS Snapshots for backups/transferring EBS volumes across Availability Zones
 2. **AMI (Amazon Machine Images)**
    - Create ready-to-use EC2 instances with your customizations
 3. **EC2 Image Builder**
    - Automatically build, test and distribute **AMIs**
 4. **EC2 Instance Store**
    - High performance **hardware disk** attached to your EC2 instance
    - Lost if your instance is stopped or terminated
 5. **EFS (Elastic File System)**
    - **Network** file system, can be attached to multiple instances in the same **Region**
 6. **EFS-IA (Elastic File System - Infrequent Access)**
    - Cost-optimized storage class for infrequent accessed files
 7. **FSx for Windows**
    - **Network** file system for Windows
 8. **FSx for Lustre (Lustre = Linux + cluster)**
    - **High Performance** Computing Linux file system
    - Machine Learning, Analytics, Video Processing, Financial Modeling,...

# ELB & ASG (Elastic Load Balancer & Auto Scaling Groups)

 1. **High Availability** vs **Scalability** (vertical and horizontal) vs **Elasticity** vs **Agility** in the Cloud
 2. **Elastic Load Balancers (ELB)**
    - Distribute across backend EC2 instances, **can be Multi-AZ**
    - Supports health checks
    - 3 Types:
      - Application Load Balancer (HTTP - Layer 7)
      - Network Load Balancer (TCP - Layer 4)
      - Classic Load Balancer (old)
 3. **Auto Scaling Groups (ASG)**
    - Implement Elasticity for your application, across multiple AZ
    - Scale EC2 instances based on demand on your system, replace unhelathy instances
    - Integrated with **ELB**

# Amazon S3 (Simple Storage Service)

 - [x] Is a object file system, all object (files) having a key that represents the path
 - [x] There is no directory within buckets
 - [x] Supports versioning

## AWS Snow Family

 1. **Data Migration**
    - Snowcone
    - Snowball Edge
    - Snowmobile
 2. **Edge Computing**
    - Snowcone
    - Snowball Edge

Service | Capacity | Notes
--------|----------|------
Snowcone | 8TB | Lightweight and small (can be used for edge computing)
Snowball Edge Compute Optimized | 42TB | Use when also is needed a device for computing
Snowball Edge Storage Optimized | 80TB | Use mainly for transfers but also has some computing capacities
Snowmobile | 100PB | Secured transport, better than Snowball if you transfer more than 10PB

## Storage Cloud Native Options

Block | File | Object
------|------|-------
Amazon EBS | Amazon EFS | Amazon S3
EC2 Instance Store | | Glacier

Service | Description
--------|------------
**Buckets** vs **Objects** | Global unique name, tied to a region
**S3 Security** | IAM Policy, S3 Bucket Policy (public access), S3 Encryption
**S3 Websites** | Host a static website on Amazon S3
**S3 versioning** | Multiple versions for files, prevents acceidental deletes
**S3 Access Logs** | Log requests made within your S3 bucket
**S3 Replication** | Same Region or Cross Region, must enable versioning
**S3 Storage Classes** | Standard, IA, One Zone-IA, Intelligent Tiering, Glacier, Glacier Deep Archive
**S3 Lifecycle Rules** | Transition Objects between Classes
**S3 Glacier Vault Lock / S3 Object Lock** | WORM (Write Once Read Many)
**Snow Family** | Import data onto S3 through a physical device, edge computing
**OpsHub** | Desktop application to manage Snow Family devices
**Storage Gateway** | Bridge between on-premise data and cloud data in S3 (File Gateway, Volume Gateway, Tape Gateway)

## S3 Storage Classes
x | S3 Standard | S3 Intelligent-Tiering | S3 Standard-IA | S3 One Zone-IA | S3 Glacier | S3 Glacier Deep Archive
--|-------------|------------------------|----------------|----------------|------------|------------------------
Minimum Storage Duration Charge | N/A | N/A | 30 days | 30 days | 90 days | 180 days
Retrieval Charge | N/A | N/A | per GB retrieved | per GB retrieved | per GB retrieved | per GB retrieved
First byte latency | milliseconds | milliseconds | milliseconds | milliseconds | select minutes or hours | select hours



