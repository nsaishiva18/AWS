# AWS

1. Intro of Course
2. Intro to DevOps and it's backstory

## 3. Client - Server Architecture

Client = Which request a resource
Server = Which respond to the resource

1-Tier - Client and Server is in same machine - It's Dead.
`2-Tier` - Client layer, Server Layer - Might get resource usage issue as app and DB in same server.
`3-Tier` - Client Layer, Application Layer and Database Layer.


## 4. DNS - Request and Response Flow

HostName
IP

DNS = Domain Name Server --> It keep tracks of all host names and IP address. DNS convert IP to Hostname to IP.

/etc/host - Local DNS has IP ---> Root Name Server(RNS) --> `.org` or `.in` or `.edu`---> Top Level Domain(.com)

.com ---> Top level Domain

Request --> Local DNS --> RNS --> Name Server(Identify the domain name) --> SOA(Start of Authority)- This has the IP.

Firewall - Which stops unauthorized access to the network. It has rules to *Allow / Deny*

`http` = 80 --> Not Secure connection to the application
`https` = 443 --> Secure Connection to the application
`SSH` = 22 --> Connect to Linux Machine
`RDP` = 3389 --> Connect to Windows Machine

data packets 

### Load Balancer

Load Balancer = Which distributes the traffic across multiple Servers

Round Robin Method.

- Request --> Firewall --> Load Balancer(DNS Name) --> Web Server --> App Server --> DB Server

`nslookup` --> To check IP address

## 5. Revision

## 6. Protocols - OSI Layers

HTTP = Hyper Text Transfer Protocol --> HTTP transfer the data to and fro from browser to server.


Data Packet --> Src, Dest, Protocol, Port, Data, Secure.

HTTPS = 443 - Certificates - SSL/TLS/HTTPS

HTTP Over TCP/IP

Transmission Control Protocol(TCP) - Establishes connection between 2 hosts, TCP is like a bridge. - TCP is Reliable.

UDP = User Datagram Protocol - UDP is not reliable.


### OSI Layers

Application - http, https
Presentation - SSH, RDP etc
Session
Transport - TCP
Network - IP
Data Link
Physical

## 7. Data Center Issues - and Cloud Evolution

P2V Migration - Physical to Virtualization

V2C Migration - Virtualization to Cloud Migration


## 8. Types of Clouds(Deployment Models) - Service Models

`AWS` - Aws is a Public cloud Provider, who provides Infrastructure as a Service (IAAS).

Virtualization
Host Machine
DNS
VM's
Infrastructure
Data Centers
Hypervisor
Load Balancer
Firewall
Protocols
WebServers
AppServers
On-Premises
Cloud
Remote Location

Physical DC --> Virtualization --> Cloud --> AWS (Remote Location(Data Centers))

### Cloud Computing

- Instead of doing computing on on-premises / local machine, we are doing computing in the remote location(Cloud) - Cloud Computing.

### Deployment Models in Cloud (Types of Clouds)

1. Public Cloud  - Services that are available for everyone like AWS, Azure, GCP etc.
2. Private Cloud - Services that are accessible with in organization like Oracle, IBM. 
3. Hybrid Cloud - Combination of Public and Private Cloud.

### Types Service Models

1. Infrastructure as a Service(IAAS)
2. Platform as a Service(PAAS)
3. Software as a Service(SAAS)

## 9. Service Models

VM's = Instances

Application
Data
OS
Virtualization = Hypervisor
Network, Data Center


VM VM VM VM VM
Hypervisor
Hardware
Physical Host Machine


### EC2 = Elastic Compute Cloud

EC2 is a AWS Service where we can launch EC2 instances(VMs).

Create = Launch

### IAAS

`Customer Responsibility` - Application, Data, OS.
`Provider Responsibility` - Virtualization, Network, Data Center.
`Shared Responsibility Model`

### PAAS

Customer - Application, Data.
Provider - OS, Virtualization, Network, Data Center.

### SAAS

Provider -  Application, Data, OS, Virtualization, Network, Data Center.

- Salesforce
- Gmail
- WebEx
- Zoom

### ElasticBeanStalk

This is a PAAS Model

- Easy and Quickly deployment of application in AWS.

3 T's

1. Elasticity  - Increasing or decreasing instances
2. Scalability - Increasing the capacity of server.
3. High Availability - Period of time service available.

## 10. Elasticity - Scalability - High Availability

### Elasticity

- Elasticity means Increasing number of Servers. It is `short term`

- Increasing and Decreasing the number of servers / instances based on the load is called `Elasticity`
- Elasticity can be achieved in AWS using `Auto Scaling`.

`Auto-Scaling` = `Scale-Out`(Increasing / Adding ) and `Scale-In`(Decreasing / Removing)

- Using the same Capacity of the servers in Auto-Scaling.

### Scalability

- Increasing the capacity of the Server.
- DB servers can only increase the capacity (8 GB RAM to 32 GB RAM)

- `Scalability` can be achieved in AWS by - Changing the instance type.

Instance Type = Combination of `Memory + CPU`

`Scalability` = `Scale-Up` and `Scale-Down`

### High Availability

- The period of time the service is `available` to the customer is called `HA`.

- The period of time the service is `Not available` to the customer is called `Downtime`.

- HA is measured in percentage.

### Redundancy

- `Redundancy` = Duplicate / having same application on different servers.

Load Balancer will do the `Health Check` for the application not Server.

200 - status code

Healthy / UnHealthy

`Monitoring` = LB will check if application is reachable or not using health checks

`FailOver` = If one server goes down, other server will take the requests sent by LB.

`High Availability` Rules = `Redundancy` + `Monitoring` + `Failover`

`0 Downtime` - `Fault Tolerance` - A System's ability to continue operating with out interruption despite the failure of one or more of it's components.

## 11. Regions and Availability Zones

AWS has Global Infrastructure.

Region --> It's a Geo-Graphical Area.

`us-east-1` - `N.Virginia` - First and Largest AWS region launched in 2006.

`ap-south-1a` - Mumbai

**Note:-** AZ's are SYNC with each other(Only Network - Not Data)

- Az's can communicated with each other by default.
- AZ's network are inter-connected.

`Latency`

Low Latency = Good
Bad Latency = Bad

**Note:-** - Regions don't communicate with each other by default, if required yes.

- LB can distribute the traffic to multiple EC2 instances across AZ's.
- LB is specific to Regional not AZ.

- EC2 --> AZ's --> VPC --> Region --> AWS

- 2 VPC's will not communicate with each other by default, if required yes.

## 12. Overview of AWS Services Part-1

1. `EC2`
EC2 = Elastic Compute Cloud
Servers = Instances / EC2 instances (VM's)

- EC2 is region specific.

2. `LB` = `ELB` - ELB distribute the traffic to multiple EC2 instances across AZ's.

- ELB is completely managed by AWS(HA, SA, Scalability, Performance etc)
- Which distribute the traffic to multiple servers.
- ELB in AWS is a Service.
- ELB can be accessible by DNS Name(URL) 
- ELB doesn't have any AZ's, it is created at regional level.

3. `ELB` - `Elastic BeanStalk` = Easy and quick deployment of application in AWS.

- In general, PAAS --> You don't have any control on the servers.
- Backbone of BeanStalk is EC2 instance.
- AWS BeanStalk --> You have full control on EC2 instances launched by BeanStalk.
- BeanStack handles EC2 instances on behalf of us.

EC2 -- Launch EC2 instances, configure, Deploy, Maintain.

BeanStalk -- Just upload the application and give same configuration

4. `LightSail` - If you want to setup and create virtual lightsail instance which already has everything installed and ready. It doesn't support Auto-Scaling.

- LightSail is readily available service in AWS.

5. `Lambda` - Serverless - We need to create F`unction` in any language but preferred is python.

- You can run the code without Server.
- Lambda function needs to be triggered or invoked.
- Lambda is used for automation's.

6. `Event Bridge` - All the events are stored.



## 13. S3 - EBS 

Floppy size - 2MB
CD's - 700MB
DVD's - 4.7GB
Pen drive - 128GB
Hard Disks - 2 TB

7. `S3 - Simple Storage Service`

- S3 is unlimited Storage by AWS
- S3 can store any kind of files(FLAT Files)
- S3 is Serverless
- AWS handles HA, Performance, Scalability etc for S3.

**Note:-** In AWS, all Services will start with `Simple` and end with `Service`.

`S3 - Simple Storage Service`
`SNS - Simple Notification Service`
`SES - Simple Email Service`

- S3 Bucket - Bucket is a container of Objects(Files)
- S3 is object based Storage and is Regional Service.
- object = File
- S3 supports static website hosing - upload all the html files.

- `Problem with S3` - We can't Run, Execute and Install. It's just a storage we can upload and download files.

8. `EBS - Elastic Block Storage`

- S3 is Object based storage, EBS is block based storage.

- Hard Disk = Volumes = EBS Volumes.

- EC2 will contain Root Volume(default volume contains OS) and Additional Volume.
- Multiple Volumes can be attached and detached.

2 types f OS's

- Client Side OS --> Win 10, 11
- Server Side OS --> Win Server 2022, 2025, Linux - Redhat, Cent OS, Ubuntu, SUSE etc...

EC2 Default volume size 

- For Win - 30GB
- For Linux - 8/10 GB

- `Max size of the EBS Volumes - 16TB`

**Note:-** : **You can not attach a volume to multiple EC2 instances at the same time**

- Volume Size can be increased on the FLY(No need to stop the EC2 instance, no downtime)

- Volume size can not be decreased(Delete the volume and re-create based on the requirement)

- Always Root volume device name of EC2 = `/dev/sda1`

- EC2 instance and EBS volume both has availability Zones, and should be in same AZ if we want to attach both.

- We can not attach 1a volume to 1b EC2 instances(Diff AZ)
- We can attach 1a volume to 1a EC2 instances(Same AZ)

- We `can not share the volume` among EC2 instances, but if need to have a shared storage we have one service in AWS that is - `EFS`

## 14. Storage and DB Services -

- `NFS - Network File System` in on-premise - Sharing file system to multiple servers.

### EFS - Elastic File System

- `EFS - Elastic File System` in AWS only for Linux. It's File based storage and unlimited storage.
- EFS works with NFS Protocol.
-`FSX`- for Windows

- EFS can be mounted to multiple EC2 instances at the same time across AZ's.
- EFS is regional but can be replicated to different regions.

### SNOW Family

- Snow Family is used to transfer huge data from On-Prem to AWS and Vice Versa.

- Snow Family is a physical Data Transfer using Devices.

1. SnowCone --> 8 TB(Size)
2. SnowEdge --> 100 TB's
3. SnowMobile --> PB's

### Glacier

- Glacier is for Archival Purpose.
- Not frequently accessed data.
- It's cheaper than S3.

- Storage Services

1. S2
2. EBS
3. Glacier
4. FSx

- These 4 storage services can be mountable to EC2.

### Storage Gateway 

- Storage Gateway is a Hybrid Storage where we can store data which is on-premise to cloud.

### Database Services

RDBMS

### RDS - Relational Database Service

`RDS - Relational Database Service` --> AWS Service where we can create Data bases.

- RDS is a service where we can setup, configure and maintain RDBMS databases.
- RDS is a database service not a database.
- RDS DB instance, RDS supports only RDBMS databases only.

- RDS Supports 7 Engines - MOMPMAI

1. MySql
2. Oracle
3. MSSQL
4. PostgreSql
5. MariaDB
6. Aurora - AWS Own DB
7. IBM DB2

### `DMS - Database Migration Service`

### DynamoDB

- `DynamoDB - NoSql database Service`(Non-Relational)
- Database = Used to store the data
- Data warehouse = It is used to store huge data.

### RedShift

- `RedShift - Data Warehouse in AWS`

### Elastic Cache

- Cache Memory = Elastic Cache - Frequently accessed data.
- Elastic Cache = `In memory database caching service`
- Low Latency 
- High Performance

- Elastic Cache has 2 Engines

1. `Redis`
2. `MemCacheD`

## 15. Route53 - VPC - CloudFront - CDN

### Route53

`Route53 is global`

- ELB --> DNS Name --> Nasty URL / Not friendly

`Route53` - It is a DNS service from AWS, DNS Port number is 53

- R53 contains records
- In R53 we do mapping

### VPC

Virtual Private Cloud

- It is like a virtual data center on cloud.
- VPC is regional
- Default VPC's in Region is `5 VPC's`
- AWS --> Region --> VPC --> AZ --> EC2

Q. How are you connecting from company to AWS ?

- Via `VPN - Shared Internet`

- `Direct Connect` - Lease Line connection from AWS which is dedicated - $16000 per month.

### CloudFront

- `CloudFront is Global`
- Edge Location will Cache the application. Both Static and Dynamic Data.

- Without CloudFront - User --> Boom.com --> Route53 --> ELB --> EC2

- With CloudFront - User --> Boom.com --> Route53 --> CF(Edge Location) ELB --> EC2

### CDN - Content Delivery Network

TTL = Time To Live 

- Invalidate Cache = Deleting the cache.
- It will be cached based on TTL Value


## 16. IAM - 

IAM = Identity and Access Management

- `Root Account` - Logins with email and password
- `IAM user` - Logins with username and password

- You can control the entire AWS using IAM by providing proper permission to the IAM Users.

- Permissions = Policies.

- `SNS = Simple Notification Service`
- `SES = Simple Email Service`
- `SQS = Simple Queue Service`
- `Trusted Advisor`
- `AWS Inspector` - To check Security.

- `Organizations` - To Manages Multiple AWS Accounts fr better management.

- Management Account - It will be one
- Member Account - Can have multiple.

- `SCP - Service Control Policies`

### CloudWatch

- CloudWatch is used to monitor all AWS Resources
- Alarms --> CPU, Network, Disk, Memory etc
- If CPU > 90% then SNS --> SMS, Email will send

- `Basic Monitoring` = You will get the data points every 5 mins, FREE[Default]
- `Detailed Monitoring` = You will get the data points every 1 min, which is billable.

### CloudTrail

- CloudTrail monitors entire AWS Account.
- Record, monitor, track, audit, logs etc.
- In laptop event viewer will log everything
- For Investigation in AWS will use CloudTrail.

### Config

- Monitor the changes in AWS resources

### Security

- Encryption can be done in 2 ways

1. `Encryption In-Transit` - While Data is traveling --> HTTPS - Certificates - `ACM - Amazon Certificate Manager`

2. `Encryption at Rest` - While data is resting --> KEYS - Encryption KEYS - `KMS - Key Management Service`

### ACM - Amazon Certificate Manager

- Service in AWS which creates certificates - ACM.

### Secret Manager 

- Secret Manager is used to store secrets(Credentials, KEYS etc)

### AWS Backup

AWS Backup = Centrally manage and automate backups

### WAF 

- WAF = Web Application Firewall
- Protect your web application from common web exploits.
- Service to stop unwanted web attacks in AWS - WAF.

### AWS Shield

- AWS Shield is used to managed DDos Protection Service.

- Basic Support - FREE
- Developer Support
- Business Support
- Enterprise Support  $15,000  - with in 15 mins issue will get resolved.


## 17. Mock Interview - Revision of Services

1. What is client ? - Which request a resource. Resource = Information.

2. What is server ? - which response to the resource

3. Can Client and server can be in different network ? - No, they should be in same network.

4. In the network components we call it as ? - Devices(can be client or server).

5. How many client-server architectures are there? - 3 types, 1-Tier(It's dead- Client and server both in same machine) 2-Tier(Client and Server in different machines - Not Secure) and 3-Tier(Client, App and Db layers - App and db communicates with IP - host ).

6. In Server we have diff layers - bottom is hardware, on top of it OS, then Application and data.

7. Diff envs - Dev, Test, Pre-Prod and Prod.

8. AWS is using `Xen` technology for virtualization.


### Key Global AWS Services

1. `AWS Identity and Access Management (IAM)`: Manages users and permissions globally.

2. `Amazon CloudFront` : A content delivery network (CDN) that delivers data through edge locations worldwide.

3. `Amazon Route 53` : A highly available and scalable cloud Domain Name System (DNS) web service.

4. `AWS Global Accelerator`: Networking service that improves application availability and performance.

5. `AWS WAF (Web Application Firewall)`: Protects web applications from exploits.

6. `AWS Shield`: Provides managed DDoS protection.
7. `AWS Organizations`: Manages multiple AWS accounts.
8. `AWS Direct Connect`: Dedicated network connection from premises to AWS.

- These services provide a consistent configuration regardless of where your application resources (like EC2 instances, which are zonal) are located.

## 18. IAM 

Identity Access Management

- `Root User` --> Full Permissions
- `IAM User` --> Limited Permissions
- IAM is Global and free
- IAM is used for Security Purpose
- With IAM, you can control entire AWS resources centrally by giving proper permissions.
- With IAM user we can login to AWS console and access any service if we have that permissions, for logging in to EC2 instance we must have EC2 
 