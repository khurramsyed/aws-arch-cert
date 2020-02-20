# AWS Certification Training
Here is list of topics that we have covered for now.


- [DNS/Route53](Route53.md)
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

### Kinesis Streams v Firehose
