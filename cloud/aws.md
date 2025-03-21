# Amazon Web Services (aws)

## overview

### compute
* EC2 (virtual servers)
* container services (run and manage docker containers)
* Lambda (run your codein response to events)
* ...

### storage
* S3 (scalable storage in the cloud)
* Glacier (low-cost archive storage in the cloud)
* EBS (block storage for EC2)
* ...

### database
* Aurora (managed relational database)
* RDS (managed relational database service for MySQL, PostgreSQL, Oracle, SQL Server, MariaDB)
* DynamoDB (managed nosql database)
* ElastiCache (in-memory data store and cache)
* ...

### network & content delivery
* Route 53 (domain name system)
* elastic load balancing
* CloudFront (global content delivery network)
* ...

## detail

### compute

#### EC2 (virtual servers)

#### container services (run and manage docker containers)
AWS container services
* https://aws.amazon.com/containers/

##### Elastic Container Service (ECS)
Amazon Elastic Container Service (Amazon ECS) is a fully managed container orchestration service that helps you to more efficiently deploy, manage, and scale containerized applications.
* https://aws.amazon.com/ecs/

#### Lambda (run your codein response to events)
Run code without thinking about servers or clusters
serverless applications - AWS Lambda is a compute service that runs your code in response to events and automatically manages the compute resources. 
* https://aws.amazon.com/lambda/
* [Introduction to AWS Lambda - Serverless Compute on Amazon Web Services](https://youtu.be/eOBq__h4OJ4)

#### Fargate
Serverless compute for containers
* https://aws.amazon.com/fargate/

#### Batch
Batch processing for ML model training, simulation, and analysis at any scale
* https://aws.amazon.com/batch/

#### elastic beanstalk
Deploy and scale web applications
* https://aws.amazon.com/elasticbeanstalk/

#### Elastic Kubernetes Service
Amazon Elastic Kubernetes Service - Start, run, and scale Kubernetes
* https://aws.amazon.com/eks/?pg=ln&sec=hiw


### storage

#### S3 (scalable storage in the cloud)
Amazon Simple Storage Service (Amazon S3) is an object storage service
* https://aws.amazon.com/s3/
* [Introduction to Amazon Simple Storage Service (S3) - Cloud Storage on AWS](https://youtu.be/77lMCiiMilo)

#### Glacier (low-cost archive storage in the cloud)

#### EBS (block storage for EC2)

#### Elastic Container Registry - docker containers
* https://aws.amazon.com/ecr/


### database

#### Aurora (managed relational database)

#### RDS (managed relational database service for MySQL, PostgreSQL, Oracle, SQL Server, MariaDB)

#### DynamoDB (managed nosql database)
* https://aws.amazon.com/dynamodb/
* Serverless, NoSQL, fully managed database
* [Tables, Items, and Attributes - Amazon DynamoDB Core Concepts | Amazon Web Services](https://www.youtube.com/watch?v=Mw8wCj0gkRc)
* [Back to Basics: Change Data Capture with Amazon DynamoDB | Amazon Web Services](https://www.youtube.com/watch?v=6YVjzD-70p4)

#### ElastiCache (in-memory data store and cache)


### network & content delivery

#### Route 53 (domain name system)
A reliable and cost-effective way to route end users to Internet applications
* https://aws.amazon.com/route53/

#### elastic load balancing

#### CloudFront (global content delivery network)


## links
* [Amazon Web Services website](https://aws.amazon.com/)
* https://github.com/aws
* [Why Build Business Applications on AWS](https://youtu.be/Mr0ZOnjwsXk)
* [Podcast: How our Site Reliability Engineers migrated GOV.UK Pay | Government Digital Service](https://gds.blog.gov.uk/2021/10/28/podcast-how-our-site-reliability-engineers-migrated-gov-uk-pay/)
* [Banking in the Cloud: 10 Lessons Learned | Jonathan Allen – AWS Enterprise Strategist and Evangelist | Amazon Web Services 2019](https://www.youtube.com/watch?v=phK8P7JQeso)


### serverless
* [Rapid Development - Why Serverless First Is Like Building with Lego](https://youtu.be/5siD210Grr4)
* [Back to Basics: Running Serverless Websites | Amazon Web Services](https://www.youtube.com/watch?v=rk9oGdfcbE4)
* [Back to Basics: Building Fan-Out Serverless Architectures Using SNS, SQS and Lambda | Amazon Web Services](https://www.youtube.com/watch?v=CEj0yyubNgQ)
* [Introduction to Amazon Kinesis](https://youtu.be/MbEfiX4sMXc)
* [Back to Basics: Event-Driven Architecture with Kinesis | Amazon Web Services](https://www.youtube.com/watch?v=uwVYQv-HRYU)


### web application
* [Back to Basics: Release Features Safely with AWS AppConfig Feature Flags | Amazon Web Services](https://www.youtube.com/watch?v=20NhUuWua_c)
* [Back to Basics: Modernizing Monolithic Applications Using Cloud Strangler Pattern | Amazon Web Services](https://www.youtube.com/watch?v=Y4CuUxiWY5w)
* [Back to Basics: Modernize Your Frontend Apps with Micro-Frontends | Amazon Web Services](https://www.youtube.com/watch?v=obb1Ps-cl2k)


### database
* [AWS re:Invent 2018: Building with AWS Databases: Match Your Workload to the Right Database (DAT301)](https://youtu.be/hwnNbLXN4vA)


### application integration

#### API Gateway
Create, maintain, and secure APIs. traffic management, CORS support, authorization and access control, throttling, monitoring, and API version management. 
* https://aws.amazon.com/api-gateway/

#### Simple Notification Service (SNS)
Fully managed Pub/Sub messaging service
* https://aws.amazon.com/sns/

#### MQ
Fully managed service for open-source message brokers
* https://aws.amazon.com/amazon-mq/
* [Getting Started with Amazon MQ - Managed Message Broker Service](https://youtu.be/iDT1zFpy1kE)


### business applications

#### Simple Email Service
Optimize your email communication with reliable, scalable, and secure solutions
* https://aws.amazon.com/ses/


### analytics

#### Open Search
ElasticSearch - real-time search, monitoring, and analysis of business and operational data
* https://aws.amazon.com/opensearch-service/
* [Amazon Elasticsearch Service](https://youtu.be/WuonfW-zQJ8)


### development tools

#### Code Commit
private Git repositories and collaborate on code
* https://aws.amazon.com/codecommit/

#### Code Pipeline
* https://aws.amazon.com/codepipeline/
* [Introduction to AWS CodePipeline - Continuous Delivery on Amazon Web Services](https://youtu.be/YxcIj_SLflw)

#### Code Build
prepackaged build environments - Build, test, package code. Create a fully automated software release process that promotes code changes through multiple deployment environments.
* https://aws.amazon.com/codebuild/

#### Code Deploy
Automate and consistently deploy your applications across your development, test, and production environments.
Support multiple deployment types, including in-place, canary, and blue/green deployments.
* https://aws.amazon.com/codedeploy/

#### Q Developer
The most capable generative AI–powered assistant for software development.
* https://aws.amazon.com/q/

#### Code Catalyst
a unified software development service.
* https://codecatalyst.aws/explore

#### Honeycode
a fully managed service that allows customers to quickly build powerful mobile and web applications – with no programming required.
* [Larry Augustin Announces Amazon Honeycode](https://youtu.be/zPupFm0BBFw)

#### Secrets Manager
Centrally manage the lifecycle of secrets
* https://aws.amazon.com/secrets-manager/
* https://docs.aws.amazon.com/secretsmanager/latest/userguide/intro.html
* https://docs.aws.amazon.com/secretsmanager/

#### Key Management Service
AWS Key Management Service (AWS KMS) is an AWS managed service that makes it easy for you to create and control the encryption keys
* https://docs.aws.amazon.com/kms/latest/developerguide/overview.html

#### Certificate Manager
AWS Certificate Manager (ACM) handles the complexity of creating, storing, and renewing public and private SSL/TLS X.509 certificates and keys
* https://docs.aws.amazon.com/acm/latest/userguide/acm-overview.html

#### Cloud Formation
Speed up cloud provisioning with infrastructure as code
* https://aws.amazon.com/cloudformation/
* [Introduction to AWS CloudFormation](https://youtu.be/Omppm_YUG2g)

#### IAM
Securely manage identities and access to AWS services and resources

* https://aws.amazon.com/iam/
