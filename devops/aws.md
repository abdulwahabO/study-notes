## Overview

AWS has both *IaaS* and *PaaS* offerings. The former allow you utilize AWS for IT infrastucture needs without having to maintaina a physical datacenter, While the latter take it a step further and remove the burden of performing adminstrative tasks on individual services.

AWS services can fall under four broad categories:

- Networking 
- Compute
- Storage
- Databases

AWS global infrastructure is divided into regions and availability zones. A `region` is a distinct geographical area which is made up of `availability zones(AZs)`. An `AZ` is datacenter or group of datacenters that operate independently with their own infrastructure like power and networking. A fault in one `AZ` will not affect operations in another.

Identity and Access Management allows AWS accounts to configure users and the AWS resources they have access to. IAM defines three(3) identities: 

- User: A person or application with keys and secrets assigned to them.
- Group: A collection of users that share a set of permissions. 
- Role: A role has specific permissions that can be assumed by users or groups.

## Compute 

**Elastic Cloud Compute (EC2)** provides resizable compute capacity. EC2 allows developers to quickly provision only the compute power they need, when they need it. The cost and complexity of managing in-house servers is removed. There are different EC2 instance types optimized for different use cases. E.g., compute optimized, storage optimized, memory optimized, etc.

**Elastic Load Balancer (ELB)** distributes network traffic between multiple targets such as EC2 instances, lambda functions, containers and IP addresses. ELB is essential to making applications scalable and robust.

**Lambda** allows developers to create event-driven functions. These so-called 'serverless' functions free developers from having to manage servers. Functions are run only when triggered by an event such as activity on an S3 bucket, API request, CloudWatch event, etc.

**Elastic Container Service (ECS)** is a scalable, fast, container service that makes it easy to manage Docker containers in a cluster. ECS can use container registries outside AWS infrastructure. 

## Storage

**Simple Secure Storage (S3)** is a service that provides scalable, secure `object storage`. An object consists of a key, data(sequence of bytes), version, metadata. Access to stored files can be configured at object or bucket level. S3 provides durable storage, high availability, encryption, versioning etc.

**Elastic Block Storage (ELB)** offers persistent `block storage` that can be attached to EC2 instances. The data on EBS volumes is replicated across multiple AZs to prevent data loss/corruption due to failure of one component. EBS is useful for databases, operating systems, enterprise applications etc.

**Elastic File Storage (EFS)** is a service that provides a shared networked file system for EC2 that is replicated across AZs.

_TODO: Block storage vs Object storage vs file storage?_

## Databases

**Relational Database Service (RDS)** makes it easy to setup and operate a relational database in the cloud. RDS offers different instance types for popular database engines e.g Postgres, MySQL, etc.

**DynamoDB** is simple NoSQL database service.

**RedShift** A service for OLAP databases that use columnar storage.

## Networking

**Route53** is a DNS service.

**CloudFront** is content delivery network for web pages and media. 

**Virtual Private Cloud (VPC)** is a way to isolate AWS services and control access to them.
