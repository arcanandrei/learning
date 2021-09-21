# Amazon Web Services - Certified Cloud Practitioner
## Table of Contents
 1. [Six advantages of Cloud Computing](#six-advantages-of-cloud-computing)
 2. [Types of Cloud Computing](#types-of-cloud-computing)
 3. [IAM - Identity Access Management](#iam---identity-access-management)
 4. [EC2 - Elastic Compute Cloud](#ec2---elastic-compute-cloud---infrastructure-as-a-service)
 5. [EC2 Instance Storage](#ec2-instance-storage)
 6. [ELB & ASG (Elastic Load Balancer & Auto Scaling Groups)](#elb--asg-elastic-load-balancer--auto-scaling-groups)
 7. [Amazon S3 (Simple Storage Service)](#amazon-s3-simple-storage-service)
 8. [Databases](#databases)
 9. [Other Compute Services](#other-compute-services)

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
&nbsp; | S3 Standard | S3 Intelligent-Tiering | S3 Standard-IA | S3 One Zone-IA | S3 Glacier | S3 Glacier Deep Archive
--|-------------|------------------------|----------------|----------------|------------|------------------------
Minimum Storage Duration Charge | N/A | N/A | 30 days | 30 days | 90 days | 180 days
Retrieval Charge | N/A | N/A | per GB retrieved | per GB retrieved | per GB retrieved | per GB retrieved
First byte latency | milliseconds | milliseconds | milliseconds | milliseconds | select minutes or hours | select hours


# Databases

 1. **RDS (Relational Database Service)** 
    - Is a Relational Database (SQL)
    - OLTP (Online Transaction Processing)
    - Managed by AWS and allows creation of
      - PostgreSQL
      - MySQL
      - MariaDB
      - Oracle
      - Microsoft SQL Server
      - Aurora (AWS Proprietary Database)
 2. **Aurora**
    - Supports PostgreSQL and MySQL
    - 5x performance improvement over MySQL on RDS
    - 3x performance improvement over PostgreSQL on RDS
    - Costs more than RDS (20%) - but more efficient
 3. **DocumentDB**
    - Same as Aurora but for MongoDB (NoSQL)
 4. **ElastiCache**
    - In-memory database that can be used for other databases other than DynamoDB
    - Helps to reduce load off database for Read-intensive workloads
 5. **DynamoDB**
    - NoSQL database (key - value stored JSON)
    - Distributed **serverless** database
    - Fast and consistent in performance, low cost
    - **DynamoDB Accelerator (DAX)**
      - 10x performance improvement
      - In-memory cache for DynamoDB
 6. **Redshift**
    - Not used for OLTP, instead used for **OLAP (online analytical processing)**
    - 10x better performance than other data warehouse, scale to PBs of data
    - Can be integrated with BI tools
 7. **EMR (Elastic Map Reduce)**
    - Create **Hadoop clusters (Big Data)**
    - Used for data processing, machine learning, web indexing, big data
 8. **Athena**
    - Fully serverless database with SQL capabilities
    - Used to query data in S3
    - Pay-per-query
 9. **QuickSight**
    - Serverless machine-learning powered business intelligence service to create interactive dashboards
 10. **Neptune**
    - Graph Database
    - Billions of relations
    - Great for knowledge graphs, fraud detection, recommendation engines, social networking
 11. **QLDB (Quantum Ledger Database)**
    - Recording financial transactions
    - No entry can be removed or modified, cryptographically verifiable
 12. **Glue**
    - Managed extract, transform and load service (ETL)
    - Fully serverless
 13. **DMS (Database Migration Service)**
    - Fully migrate databases
    - The source database remains available during the migration

Service | Type | Best used for | Serverless | Managed | Notes
--------|------|---------------|------------|---------|------
RDS | SQL | Traditional applications | | [x] | Relational database
Aurora | SQL | Traditional applications | | [x] | PostgreSQL & MySQL compatible
DocumentDB | NoSQL | Content management | | [x] | MongoDB compatible
DynamoDB | NoSQL | High traffic web apps, e-commerce, gaming | | [x] | Fast and consistent, low-latency
Redshift | SQL | Data warehouse, scale to PBs of data | | [x] | Columnar storage of data, OLAP
Athena | SQL | Query data in S3 | [x] | [x] | Pay per query
QLDB | SQL | Record financial transactions | [x] | [x] | No entry can be modified or removed
Neptune | Graph | Recommendation engines, Social netorks | | [x] | Billions of relations and query with milliseconds latency
ElastiCache | Caching | Caching, session management, gaming leaderboards | | [x] | High performance, Redis or Memcached
EMR | Process | Data Processing, Machine Learning, Big Data | | [x] | Create Hadoop clusters (Big Data)
QuickSight | Process | Create interactive dashboards | [x] | [x] | Integrated with RDS, Aurora, Athena, Redshift, RDS
Glue | Process | Prepare and transform data for analytics | [x] | [x] | Extract, transform and load (ETL) 
DMS | Process | Migrate databases to AWS | | [x] | Supports both homogeneous and heterogeneous migrations

# Other Compute Services

Service | Description | Notes
--------|-------------|------
**ECS (Elastic Container Service)** | Run Docker containers on EC2 instances | 
**Fargate** | Run Docker containers without provisioning the infrastructure | Serverless offering (No EC2 instances)
**ECR (Elastic Container Registry)** | Private Docker Images Repository | 
**Batch** | Run Batch jobs on AWS across managed EC2 instances |
**Lightsail** | Predictable & Low-pricing for simple application & DB stacks |

## AWS Lambda

 1. Lambda is **serverless**
 2. **Lambda billing**
    - By the time run * by the RAM provisioned
    - By the number of invocations
 3. **Language support**
    - Many programming languages except (arbitrary) Docker
 4. **Invocation time**
    - Up to **15 minutes**
 5. **Use cases**
    - Create thumbnails for images uploaded onto S3
    - Run a **serverless** cron job
 6. **API Gateway**
    - Expose Lambda functions as **HTTP API**

# Deployment

Service | Description | Platform | Notes
--------|-------------|----------|------
**CloudFormation** | IaaS, works with almost all AWS resources | AWS | Can be repeated across regions and accounts
**BeanStalk** | PaaS, limited to certain programming languages or Docker | AWS | Deploy code consistently with a known architecture, developer is responsible only for the application code
**CodeDeploy** | Deploy & Upgrade any application onto servers | Hybrid | 
**Systems Manager** | Patch, Configure & Run commands at scale | Hybrid | Get operational insights about the state of your infrastructure
**OpsWorks** | Managed Chef & Puppet in AWS | Hybrid | Chef & Puppet in exam -> OpsWorks

# Developer services

Service | Description
--------|------------
**CodeCommit** | Store code in private GIT repository (version controlled)
**CodeBuild** | Build & Test code in AWS
**CodeDeploy** | Deploy code onto servers
**CodePipeline** | Orchestration of pipeline (from code to build to deploy)
**CodeArtifact** | Store software packages & dependencies on AWS
**CodeStar** | Unified view for allowing developers to do CI/CD & code
**Cloud9** | Cloud IDE with collaboration possibility
**AWS CDK** | Define your cloud infrastructure using a programming language

# Global Applications

 1. **Route 53**
    - Global DNS
    - Great to route users to the closest deployment with least latency
    - Grest for disaster recovery strategies
 2. **CloudFront**
    - Global **Content Delivery Network (CDN)**
    - Replicate part of your applications to AWS Edge Locations - decrease latency
    - Cache common requests - improved user experience and decreased latency
 3. **S3 Transfer Acceleration**
    - Accelerate global uploads & downloads into **Amazon S3**
 4. **AWS Global Accelerator**
    - Improve global application availability & performance using the AWS global network
 5. **AWS Outposts**
    - Deploy Outposts Racks in your own Data Centers to extend AWS services
 6. **AWS WaveLength**
    - Brings AWS services to the edge of 5G networks
    - Ultra low-latency applications

# Cloud Integration

 1. **SQS (Simple Queue Service)**
    - Queue service in AWS
    - Multiple Producers, messages are kept up to 14 days
    - Multiple Consumers share the read and delete messages when done
    - Used to **decouple** applications in AWS
 2. **SNS (Simple Notification Service)**
    - Notification service in AWS
    - Subscribers: Email, Lambda, SQS, HTTP, Mobile,...
    - Multiple Subscribers, send all messages to all of them
    - **No message retention**
 3. **Kinesis**
    - Real-time data streaming, persistence and analysis
 4. **Amazon MQ**
    - Managed Apache MQ in the cloud (MQTT, AMQP protocols)
    - Used to easily migrate to the cloud instead of re-engineering the application to use SQS or SNS

# Cloud Monitoring

 1. **CloudWatch**
    - **Metrics**
      - Monitor the performance of AWS services and billing metrics
    - **Alarms**
      - Automate notification, perform EC2 action, notify to SNS based on metric
    - **Logs**
      - Collect log files from EC2 instances, servers, Lambda functions,...
    - **Events (or EventBridge)**
      - React to events in AWS, or trigger a rule on a schedule
 2. **CloudTrail**
    - Audit API calls made within your AWS account
 3. **CloudTrail Insights**
    - Automated analysis of your CloudTrail events
 4. **X-Ray**
    - Trace requests made through your distributed applications
 5. **Service Health Dashboard**
    - Status of all AWS services across all regions
 6. **Personal Health Dashboard**
    - AWS events that impact your infrastructure
 7. **Amazon CodeGuru**
    - Automated code reviews and application performance recommendations

# VPC

# Security & Compliance

# Machine Learning

# Management, Billing & Support

# Advanced Identity

# Other AWS Services

# AWS Architecting & Ecosystem

## AWS Well-Architected Pillars


