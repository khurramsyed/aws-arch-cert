# AWS Certification Training
Here is list of topics that we have covered for now.

- [Aurora](Aurora.md)
- [AWSGlue](AWSGlue.md)
- [CloudWatch](CloudWatch.md)
- [DNS/Route53](Route53.md)
- [Kinesis](Kinesis.md)
- [VPC](VPCNotes.md)
- [Athena - Query Your unstructured Data using ANSI SQL](amazonAthena.md)
- [Simple Storage Service- S3](s3.md)
- [Monitoring AWS CloudWatch](CloudWatch.md)
- [ETL Across AWS Data Stores - Using AWS Glue](AWSGlue.md)
- [Kinesis - Streams and Firehose](Kinesis.md)
- [EC2](EC2Notes.md)
- [HAArchitecture](HAArchitecture.md)

## To Revise
- [Areas to Focus](problems.md)
### Good Links
- [AWS 10-Minute Tutorials](https://aws.amazon.com/getting-started/tutorials/?awsf.getting-started-content=*all)


# Comparisons
### EMR V Athena V Glue V Redshift Spectrum v S3 Select
- `Elastic Map Reduce (EMR)` is used for `processing and analyzing` data using the Hadoop framework. It is  **NOT** `used for transforming` streaming data. `Quickly & cost-effectively process vast amounts` of data. It does **`NOT`** provide the ability to process your data in real-time, unlike Kinesis. Compute-optimized instances are ideal for compute-bound applications that benefit from high-performance processors but not for analyzing clickstream data from various websites in real-time.

- `Amazon Athena` is an interactive query service that makes it easy to `analyze data in Amazon S3 using standard SQL`. Athena is serverless, so there is no infrastructure to manage, and you `pay only for the queries that you run`.
- AWS Glue is a fully managed `extract, transform, and load (ETL)` service that makes it easy for customers to prepare and load their data for analytics.
- AWS Glue natively supports data stored in `Amazon Aurora and all other Amazon RDS engines, Amazon Redshift, and Amazon S3, as well as common database engines and databases` in your Virtual Private Cloud (Amazon VPC) running on Amazon EC2.
- `S3 Select` Just to selectively load the data from S3.
- `RedShift Spectrum` - Works on Redshift External tables/data stored in S3.

### When to Use Which storage Type

![alt ](images/StorageTypeSelection.png)    

### Shared Responsibility Model

Security and Compliance is a shared responsibility between AWS and the customer. This shared model can help relieve customer’s operational burden as AWS operates, manages and controls the components from the host operating system and virtualization layer down to the physical security of the facilities in which the service operates. The customer assumes responsibility and management of the guest operating system (including updates and security patches), other associated application software as well as the configuration of the AWS provided security group firewall.

Customers should carefully consider the services they choose as their responsibilities vary depending on the services used, the integration of those services into their IT environment, and applicable laws and regulations. The nature of this shared responsibility also provides the flexibility and customer control that permits the deployment. This differentiation of responsibility is commonly referred to as Security “of” the Cloud versus Security “in” the Cloud.

The **`shared responsibility`** model for infrastructure services, such as Amazon Elastic Compute Cloud (Amazon EC2) for example, specifies that AWS manages the security of the following assets:

- Facilities
- Physical security of hardware
- Network infrastructure
- Virtualization infrastructure

You as the customer are responsible for the security of the following assets:

- Amazon Machine Images (AMIs)
- Operating systems
- Applications
- Data in transit
- Data at rest
- Data stores   
- Credentials
- Policies and configuration

For a better understanding about this topic, refer to the AWS Security Best Practices [whitepaper](https://d0.awsstatic.com/whitepapers/aws-security-best-practices.pdf) on the reference link below and also the Shared Responsibility Model diagram:

![alt Shared Responsibility Model](images/Shared_Responsibility_Model.jpg)

### AWS Inspector Agent

AWS Inspector Agent in each instance which will collect and push data to CloudWatch Logs periodically. AWS Inspector is simply a security assessments service which only helps you in checking for unintended network accessibility of your EC2 instances and for vulnerabilities on those EC2 instances.

https://tutorialsdojo.com/aws-cheat-sheet-cloudwatch-agent-vs-ssm-agent-vs-custom-daemon-scripts/



### SAML Compatiblity

If your identity store is not compatible with SAML 2.0, then you can build a custom identity broker application to perform a similar function. The broker application authenticates users, requests temporary credentials for users from AWS, and then provides them to the user to access AWS resources.

The application verifies that employees are signed into the existing corporate network's identity and authentication system, which might use LDAP, Active Directory, or another system. The identity broker application then obtains temporary security credentials for the employees.

To get temporary security credentials, the identity broker application calls either AssumeRole or GetFederationToken to obtain temporary security credentials, depending on how you want to manage the policies for users and when the temporary credentials should expire. The call returns temporary security credentials consisting of an AWS access key ID, a secret access key, and a session token. The identity broker application makes these temporary security credentials available to the internal company application. The app can then use the temporary credentials to make calls to AWS directly. The app caches the credentials until they expire, and then requests a new set of temporary credentials.

![alt ](images/identity_auth_Non_Saml.diagram.png)


### SQS VS AMAZON MQ

Amazon MQ, Amazon SQS, and Amazon SNS are messaging services that are suitable for anyone from startups to enterprises. If you're using messaging with existing applications and want to move your messaging service to the cloud quickly and easily, it is recommended that you consider Amazon MQ. It supports industry-standard APIs and protocols so you can switch from any standards-based message broker to Amazon MQ without rewriting the messaging code in your applications.

>Amazon MQ is suitable for enterprise IT pros, developers, and architects who are managing a message broker themselves–whether on-premises or in the cloud–and want to move to a fully managed cloud service without rewriting the messaging code in their applications.







### TO READ/REVISE
What functions can be performed on keys.
AWS Budget Cost Explorer and Cost allocation tags
How is DynamoDB performance and sacalibility provided.
S3 Summary

Structrue of Cloud Formantion Template
Dynamo DB Partitioning
When using EC2 instances with Dedicated Hosting, which of the following modes are you able to transition between by stopping the instance and starting it again?

EBS Cycle Policy
EC2 Scaling cool down and warm up period
shared responsibility model
Bastion Host Where should it be installed (I think public subnets )
Read Load Balancers which ones will be cross region/cross az
DNS Record types
ENhanced RDS monitoring
 Lambda function is storing sensitive database and API credentials,
 Which Amazon Services are fully managed
 Red Shift Query Queues
 LONG POLLING V SHORT POLLING
 SCALING Policies
CloudFormation COMPONENT AND termS
Cloud Formation Template vs Stack
VPC Endpoint
Interface Endpoint
NAT Gateway and NAT Instance configuration
EMR ,Neptune , Athena are these serverless?
How to monitor memory in cloud watch
EC2 Enhanced Networking
Placement Group (Insufficient capacity
Amazon Stoarge Gateway

You have triggered the creation of a snapshot of your EBS volume attached to an Instance Store-backed EC2 Instance and is currently on-going. At this point, what are the things that the EBS volume can or cannot do

Blue green , CAnary , In place release
RDP Port 3389
Cloud HSM v KMS
AWS Security Token Service  
EMR vs Glue V Athena
Launch configurations and ASG
Ealsticache Redis Multi Az and

S3 V EBS v EFS (use cases atleast)
IAM Policy vs bucket policies


https://docs.aws.amazon.com/AmazonS3/latest/dev/UsingEncryption.html

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSEncryption.html

https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-public-data-sets.html


https://aws.amazon.com/about-aws/whats-new/2018/11/amazon-cloudfront-announces-support-for-origin-failover/



FileGateway
