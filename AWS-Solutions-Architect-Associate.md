## AWS Services

| Service | Description |
| ------- | ----------- |
| AWS AppFlow | Automate the exchange of data between SaaS vendors and AWS services |
| AWS Artifact | Compliance-related information and reports |
| Amazon Athena | Analyze S3 data using SQL queries |
| AWS Audit Manager | Automated service to produce reports for audits |
| AWS Batch | For longer batch workloads (>15 minutes) that Lambda can't run |
| AWS Budgets | Set budgets and alerts when costs exceed (or are forecasted to exceed) the budget |
| AWS CloudHSM | Hardware Security Module Service |
| AWS CloudTrail | Event history for AWS services |
| AWS CloudWatch | Monitoring and Alarms |
| AWS Cognito | Auth and user management (including federation/IdP) for applications |
| AWS Comprehend | Natural-language processing to help understand the meaning/sentiment of text |
| AWS Compute Optimizer | Automated collection of metrics for underutilized compute instances |
| AWS Cost and Usage Reports | Detailed cost and spending reports |
| AWS Database Migration Service | Migrate your database to AWS |
| AWS Detective | Analyze and investigate potential security issues |
| AWS Direct Connect | Private, direct connection (not internet) between your facilities and AWS |
| AWS Elastic Block Storage (EBS) | Block storage for EC2 instances |
| AWS Elastic Cloud Compute (EC2) | Cloud computing/severs |
| AWS Elastic Map Reduce | Export and import data between DynamoDB instances |
| AWS ECS Fargate | Run containers without managing EC2 instances |
| AWS ElastiCache | In-memory, caching service |
| Amazon Elastic Transcoder | Convert media files into different formats |
| Amazon Fraud Detector | AI-based fraud detection |
| AWS Firewall Manager | Security firewall management service across multipe applications and accounts |
| Amazon Forecast | Time-series forecasting leveraging machine learning |
| AWS Inspector | Automated security assessment service |
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
| AWS Network Firewall | Firewall infrastructure managed by AWS |
| AWS Personal Health Dashboard | Alerts and guildance when AWS services go down |
| AWS Polly | Text-to-speech service |
| AWS Quantum Ledger Database (QLDB) | Immutable, cryptographically verifiable log of data changes |
| AWS Redshift | Fully-managed, petabyte-scale data warehouse |
| AWS S3 | Simple Storage Service - Object storage |
| Amazon SageMaker | Build, train, and deploy machine learning models |
| AWS Snowball | Physical storage device to upload data into and send to Amazon for download into AWS |
| AWS Snowball Edge | Snowball with compute power for select AWS capabilities |
| AWS SNS | Simple Notification Service - Send (push) messages and emails |
| AWS SQS | Simple Queue Service |
| AWS Step Functions | Workflow orchestation for Lambda |
| AWS STS | Provide trusted users with temporary credentials to access AWS resources |
| AWS Transcribe | Speech-to-text service |
| AWS Tranaslate | Machine learning service to automate language translation |
| AWS Trusted Advisor | Realtime guidance to provision resources following best practices |
| AWS X-Ray | Detailed information on Lambda functions |

## Alexa

* Alexa is built from Amazon Lex, Amazon Polly, and Amazon Transcribe

## AppSync

* AppSync supports deploying a GraphQL interface

## CloudWatch

* Memory utilization metric is not available out-of-the-box
	* You have to create a custom metric for memory, disk swap, disk space, page file, and log utilization

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
* Get information about scripts used to bootstrap instances with `http://169.254.169.254/latest/user-data
* There are vCPU-based on-demand instance limits per region
	* These service quotas are defaults and can be expanded
* Reboot will not cause data loss on an ephemeral EC2 instance
* EBS supports point-in-time snapshots that can save data while destroying the attached EC2 instance
* If stuck in a contract for reserved instances, you can sell the instances on the Reserved Instance Marketplace
* Spot instances are cheaper during off-hours, times when AWS is less-busy
* If AWS needs to reboot an instance for underlying hardware maintenance, set up an EventBridge rule that is triggered by the AWS Health event. Set up a lambda to parse the event and reboot the EC2 instance.
* You can hot attach an ENI from one instance to another instance
* A placement group will allow instances to be close to each other

## ECS (Fargate)

* Easy to scale container workloads on-demand

## EKS

* Amazon EKS Distro is a Kubernetes distrbution that you can run on-prem

## IAM

* IAM users and groups can be assigned policies
* IAM users should be placed into groups and policies assigned to those groups for better management

## Kinesis Data Firehose

* Can't stream to Athena
    * Athena is for queries

## NACLs

* NACL is evaluated by rule number **lowest to highest*
* NACL is executed immediately when a matching rule is found
* Default NACL is Allow
* Default config for custom NACL is Deny
  * `All Traffic Deny` final rule of default NACL cannot be modified
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

## SageMaker

* SageMaker has a different savings plan than the compute savings plan

## SNS

* Does not support Apache Kafka messaging protocols

## SQS

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
