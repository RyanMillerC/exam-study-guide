## AWS Services

| Service | Description |
| ------- | ----------- |
| AWS AppFlow | Automate the exchange of data between SaaS vendors and AWS services |
| AWS AppSync | Scalable GraphQL interface to combine data from multiple sources like DynamoDB, Lambda, and HTTP APIs |
| AWS Artifact | Compliance-related information and reports |
| Amazon Athena | Analyze S3 data using SQL queries |
| AWS Audit Manager | Automated service to produce reports for audits |
| Amazon Aurora | Managed MySQL and PostgreSQL compatible DB |
| Amazon Aurora Serverless | On-demand, autoscaling configuration for Amazon Aurora |
| AWS Batch | For longer batch workloads (>15 minutes) that Lambda can't run |
| AWS Budgets | Set budgets and alerts when costs exceed (or are forecasted to exceed) the budget |
| AWS CloudHSM | Hardware Security Module Service |
| AWS CloudTrail | Event history for AWS services |
| AWS CloudWatch | Monitoring and Alarms |
| AWS Cognito | Auth and user management (including federation/IdP) for applications |
| AWS Comprehend | Natural-language processing to help understand the meaning/sentiment of text |
| AWS Compute Optimizer | Automated collection of metrics for underutilized compute instances |
| AWS Control Tower | Set up and govern multi-account environments |
| AWS Cost and Usage Reports | Detailed cost and spending reports |
| AWS Data Pipeline | Data driven workloads that automatically move data between AWS services |
| AWS Database Migration Service | Migrate your database to AWS |
| AWS Detective | Analyze and investigate potential security issues |
| AWS Direct Connect | Private, direct connection (not internet) between your facilities and AWS |
| Amazon DocumentDB | NoSQL JSON object document DB compatible with MongoDB workloads |
| AWS Elastic Block Storage (EBS) | Block storage for EC2 instances |
| AWS Elastic Cloud Compute (EC2) | Cloud computing/severs |
| AWS Elastic Map Reduce | Export and import data between DynamoDB instances |
| AWS ECS Fargate | Run containers without managing EC2 instances |
| AWS ElastiCache | In-memory, caching service |
| Amazon Elastic Transcoder | Convert media files into different formats |
| Amazon EventBridge | Serverless way to string events to connect application components |
| Amazon Fraud Detector | AI-based fraud detection |
| AWS Firewall Manager | Security firewall management service across multipe applications and accounts |
| Amazon Forecast | Time-series forecasting leveraging machine learning |
| Amazon FSx | Highly-performant file systems |
| Amazon GuardDuty | Security monitoring (via CloudTrail, logs, etc.) for other AWS services |
| AWS Inspector | Automated security assessment service (vulnerabilities, network exposure, etc.) for workloads |
| Amazon Kendra | Intelligent enterprise search powered by machine learning |
| Amazon Keyspaces | Scalable, highly-available, managed Apache Cassandra compatible database service |
| AWS Kinesis Data Analytics | Real-time analytics on data |
| AWS Kinesis Data Firehose | Load streaming data into data stores and anayltics tools |
| AWS Kinesis Data Streams | Stream log/event data and take action on that data |
| Amazon Kinesis Video Streams | Stream media content from a large number of devices for anayltics and processing |
| AWS Lex | Build conversational interfaces in applications with natural-language models |
| AWS Macie | Check for sensitive data in S3 buckets |
| Amazon MQ | Managed broker service (Like RabbitMQ, ActiveMQ) |
| AWS Managed Grafana | AWS managed Grafana instance |
| AWS Managed Service for Prometheus | AWS managed Prometheus |
| AWS Managed VPN | High availability VPN service allowing customers to use existing VPN equipment |
| AWS MSK | Amazon Managed Streaming for Apache Kafka |
| Amazon Neptune | Serverless graph database |
| AWS Network Firewall | Firewall infrastructure managed by AWS |
| AWS Organizations | Service to manage existing AWS accounts for multi-account organizations |
| AWS Personal Health Dashboard | Alerts and guildance when AWS services go down |
| AWS Polly | Text-to-speech service |
| AWS Quantum Ledger Database (QLDB) | Immutable, cryptographically verifiable log of data changes |
| AWS Redshift | Fully-managed, petabyte-scale data warehouse |
| AWS S3 | Simple Storage Service - Object storage |
| Amazon SageMaker | Build, train, and deploy machine learning models |
| AWS Security Hub | Cloud security posture management service |
| AWS Service Catalog | Catalog of approved services available to users typically deployed through CloudFormation templates |
| AWS Sheild | DDoS protection service |
| AWS Snowball | Physical storage device to upload data into and send to Amazon for download into AWS |
| AWS Snowball Edge | Snowball with compute power for select AWS capabilities |
| AWS SNS | Simple Notification Service - Send (push) messages and emails |
| AWS SQS | Simple Queue Service |
| AWS Step Functions | Workflow orchestation for Lambda |
| AWS STS | Provide trusted users with temporary credentials to access AWS resources |
| Amazon Textract | Automatically extract printed text, handwriting, and data from any document |
| AWS Transcribe | Speech-to-text service |
| AWS Tranaslate | Machine learning service to automate language translation |
| AWS Trusted Advisor | Realtime guidance to provision resources following best practices |
| AWS WAF | Web Application Firewall service |
| AWS X-Ray | Detailed information on Lambda functions |

## Alexa

* Alexa is built from Amazon Lex, Amazon Polly, and Amazon Transcribe

## AppSync

* AppSync supports deploying a GraphQL interface

## CloudFront

* Signed cookies are great for accessing multiple files

## CloudWatch

* Memory utilization metric is not available out-of-the-box
    * You have to create a custom metric for memory, disk swap, disk space, page file, and log utilization
* CloudWatch will monitor while CloudTrail will track resources and log

## Control Tower

* Control Tower and Organziations have some overlap
    * Control Tower is newer
    * Control Tower can create new AWS accounts
    * Control Tower can impose restrictions on AWS accounts
    * Organizations is better if you already have a bunch of AWS accounts

## Cognito

* Authentication process
    1. - Authenticate and get tokens
    2. - Exchange tokens and get AWS credentials
    3. - Access AWS services using credentials

## Database Migration Service

* Supports homogeneous migrations (E.g. Oracle to Oracle)
* Supports heterogeneous migrations (E.g. Oracle to Amazon Aurora)

## DynamoDB

* Performant key-value database

## EC2

* Application Load Balancers (ALB) only send traffic to instances that respond to health checks
    * If an application stops responding, the ALB will stop sending traffic until it's healthy again
    * ALB **will not** terminate an instance that is unhealthy
* For performance sensitive, low-latency applications, use a Network Load Balancer
* When an auto-scaling group (ASG) scales down EC2 instances, the oldest configured instance will be terminated first
* Security Groups are stateful
    * Responses to outgoing requests are not subject in incoming request rules
* Security Groups can be updated while an instance is running
* Up to 5 Security Groups can be assigned to an EC2 instance
* Get information about scripts used to bootstrap instances with `http://169.254.169.254/latest/user-data`
* Get information about the instance itself with `http://169.254.169.254/latest/meta-data`
* There are vCPU-based on-demand instance limits per region
    * These service quotas are defaults and can be expanded
* Reboot will not cause data loss on an ephemeral EC2 instance
* If stuck in a contract for reserved instances, you can sell the instances on the Reserved Instance Marketplace
* Spot instances are cheaper during off-hours, times when AWS is less-busy
* If AWS needs to reboot an instance for underlying hardware maintenance, set up an EventBridge rule that is triggered by the AWS Health event. Set up a lambda to parse the event and reboot the EC2 instance.
* You can hot attach an ENI from one instance to another instance
* A placement group will allow instances to be close to each other
* EBS
    * EBS supports point-in-time snapshots that can save data while destroying the attached EC2 instance
    * EBS volumes can be used normally while a snapshot is in progress
    * EBS multi-attach can be used to attach an EBS volume to multiple instances
    * io2 Block Express is the fastest, most performant type of EBS volume
* Instance Types
    * M/T - General purpose
    * C - Compute optimized
    * R/X - Memory optimized
* Autoscaling Groups
    * Target tracking scaling will target a specific metric and scale instances based on that

## ECS (Fargate)

* Easy to scale container workloads on-demand

## EKS

* Amazon EKS Distro is a Kubernetes distrbution that you can run on-prem

## FSx

* Supports Windows file storage (CIFS)
* Also supports NetApp ONTAP, OpenZFS, and Lustre
* Lustre is good for high performance data sets (ex. active ML models)

## GuardDuty

* Continuous security monitoring that acts as an intrusion detection service

## IAM

* IAM users and groups can be assigned policies
* IAM users should be placed into groups and policies assigned to those groups for better management
* IAM database authentication allows an RDS DB to only be accessed with profile credentials specific to EC2 instances

## Inspector

* Scans and reports on vulnerabilities and network exposure
* This is NOT an intrusion detection service

## Keyspaces

* Apache Cassandra and Amazon Keyspaces are NoSQL databases for massive amounts of data

## Kinesis Data Firehose

* Can't stream to Athena
    * Athena is for queries

## Organizations

* You can enable consolidated billing to pool resource utilization between multiple AWS accounts in an organziation
    * This might lower costs

## NACLs

* NACL is evaluated by rule number **lowest to highest**
* NACL is executed immediately when a matching rule is found
* Default NACL is Allow
* Default config for custom NACL is Deny
* `* All Traffic Deny` final rule of default NACL cannot be modified
* NACLs are stateless
    * Responses to outgoing requests are subject to NACLs

## RDS

* Multi-AZ deployments provide high-availability for RDS database instances
* Multi-AZ MySQL automatically provisions a synchronus standby replica in a different AZ
* You can create a read replicate in a different AZ to point read workloads at

## Route 53

* Route 53 supports geolocation routing

## S3

* Notifications can be enabled for restore operations from Glacier
* Glacier is best for infrequently accessed data and archival data
* For large transfers, use multipart upload
* For huge transfers, a Snowball device may be a better option than uploading data
* Transfer Acceleration is good for gigabyte/terabyte uploads from all over the world
* Put CloudFront in front of S3 for simple static web hosting
* Presigned URLs with expiry dates can prevent abuse from hotlinking to S3 resources

## SageMaker

* SageMaker has a different savings plan than the compute savings plan

## Sheild

* Sheild Advanced has a dedicated team to respond to attacks

## SNS

* Does not support Apache Kafka messaging protocols

## SQS

* SQS supports 2 types of message queue
    * Standard - maximum throughput
    * FIFO - Processed in order and processed exactly once
* SQS Standard handles extereme performance (e.g. 50,000 requests per second)
* SQS FIFO can't handle that same level of performance

## STS

* Should be used for temporary credentials
* Can last a few minutes or a few hours
* IAM should be used for longer-term credentials

## VPC

* Each subnet in your VPC must be associated with a network ACL
    * If one isn't specified the default is used
* A VPC has a default security group that can be modified but not deleted
* VPC endpoints can be configured to allow instances to hit AWS services directly, without going through the internet

## WAF

* A rate-based rule can limit an IP to x number of requests per y time interval
