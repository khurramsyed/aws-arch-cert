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
### EMR V Athena V Glue
- `Elastic Map Reduce (EMR)` is used for `processing and analyzing` data using the Hadoop framework. It is  **NOT** `used for transforming` streaming data.
- `Amazon Athena` is an interactive query service that makes it easy to `analyze data in Amazon S3 using standard SQL`. Athena is serverless, so there is no infrastructure to manage, and you `pay only for the queries that you run`.
- AWS Glue is a fully managed `extract, transform, and load (ETL)` service that makes it easy for customers to prepare and load their data for analytics.
- AWS Glue natively supports data stored in `Amazon Aurora and all other Amazon RDS engines, Amazon Redshift, and Amazon S3, as well as common database engines and databases` in your Virtual Private Cloud (Amazon VPC) running on Amazon EC2.

### Shared Responsibility Model

Security and Compliance is a shared responsibility between AWS and the customer. This shared model can help relieve customer’s operational burden as AWS operates, manages and controls the components from the host operating system and virtualization layer down to the physical security of the facilities in which the service operates. The customer assumes responsibility and management of the guest operating system (including updates and security patches), other associated application software as well as the configuration of the AWS provided security group firewall.

Customers should carefully consider the services they choose as their responsibilities vary depending on the services used, the integration of those services into their IT environment, and applicable laws and regulations. The nature of this shared responsibility also provides the flexibility and customer control that permits the deployment. This differentiation of responsibility is commonly referred to as Security “of” the Cloud versus Security “in” the Cloud.

The shared responsibility model for infrastructure services, such as Amazon Elastic Compute Cloud (Amazon EC2) for example, specifies that AWS manages the security of the following assets:

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



### TO READ/REVISE
What functions can be performed on keys.
How is DynamoDB performance and sacalibility provided.
Which of the following are valid S3 data encryption options? [Select 4]
S3 Disk Types and performance
S3 Pricing
S3 Srorage classes
Structrue of Cloud Formantion Template
WHich IP Address AWS reserves in a VPC
Dynamo DB Partitioning
When using EC2 instances with Dedicated Hosting, which of the following modes are you able to transition between by stopping the instance and starting it again?
Amazon Stoarge Gateway
EBS Cycle Policy
EC2 Scaling cool down and warm up period
shared responsibility model
Bastion Host Where should it be installed (I think public subnets )
Read Load Balancers which ones will be cross region/cross az
DNS Record types


FileGateway
