# AWS Services

## AWS Compute

Compute comprises of

- EC2
- EC2 Container Services
- Elastic Beanstalk
- Lambda
- Lightsail
- Batch


## EC2
   EC2 is typicaly virtual machines , though you can have dedicated physcial machines , however typically it is virtual machines that we will use.

## EC2 Container Services
EC2 Container Services - Docker containers at scale.


## ELastic Beanstalk

ELastic Beanstalk is a for developers who don't understand AWS , So these developer will just upload the application and Elastic Beanstalk will do auto provisioning, autoscaling and creating EC2 instanaces.

## Lambda
Lambda is code that you upload to cloud and then you control whne it executes , you dont have to worry about any virtual or physical mahcines or operating systems. All you worry about is the code.
We will use lamabda , architect and dev associate courese. Take as much notes as you can into text editor , we will upload to website and these notes will then turn it into audio and then you can download it and listen to it. We will also learn how to turn that audio into something that alexa can read those notes to you. So you can invoke your own alex school, so alexa can help you with your sutdies.

## Lightsail
Lightsail is amazon's VPS (Virtual Private Server) Service , designed for people who do not want to understand anything about AWS and the infrstructure. so this will provision you with a server and fixed IP address, and provide you will RDP access for windows and ssh access for linux and come with management console , you can think of it as a lightweight version of EC2.

## Batch
Batch is used for batch computing in the cloud , however not convered in any of the certification courses.



# AWS Storage

## S3 - is the oldest storage service, we have something called bucket ,you upload files in buckets. Object based storage.
## EFS - Electronic file systems , which is NAS , so you can store file on EFS storage and mount on different machine.
## Glacier , is data archival , Archive data that you dont need it or check very infrequency
## Snowball , If you are bringing Large amount of data e.g into AWS data center. rather than transmitting it over the wire, you bring in the disk and  they will send to AWS data center and import manually.
## Storage gateway is virtual mahcine that you install in your datacenter or head office and that will replicate into S3


## Databases

RDS :
Ralational Databases Service , includling mySQL, PogresSQl , amazon version of database called aurora which is compatible with mySQL as well.	, any RDBMS will sit like Oracel, SQL Server.

DynamoDB :
non relational db.

Elasticache:
way of caching commonly queried data. will free up database service to do other work

Redshift:
Dataware housing or BI , really complex queries ,e.g. profit and loss.


# Migration:

AWS Migration Hub:
Tracks your applcation as you migrate into AWAS , plus it integrates with other services in AWS to help with migration.

Application Discovery Service:
Automated ,tracks  detects applications and its dependencies.

Database Migration:

Migrates DBs from on premise to AWS.  AWS migration Service helps you migrated your virtual or physical database for this.

Server Migration Service:
Snowball:

Between Storage and migration , migrates large amount of data in AWS.

## Networking and Content Delivery:

VPC:

Amazon Virtual private cloud, pretty complicated you need to build it to pass exam. very important.

Cloud Front :

is Content Delivery Network, meida assets are stored in egde location based on where you are in the world.

Route 53:
is Amazon DNS

API Gateway:
Very important

Direct Connect:
is very big for Arch exam. way of running a dedicated line from office to AWS and into VPC.

### CloudFront (Signed URL Vs Signed cookies)

CloudFront signed URLs and signed cookies provide the same basic functionality: they allow you to control who can access your content. If you want to serve private content through CloudFront and you're trying to decide whether to use signed URLs or signed cookies, consider the following:

**Use signed URLs for the following cases:**

- You want to use an RTMP distribution. Signed cookies aren't supported for RTMP distributions.
- You want to restrict access to individual files, for example, an installation download for your application.
- Your users are using a client (for example, a custom HTTP client) that doesn't support cookies.

**Use signed cookies for the following cases:**
- You want to provide access to multiple restricted files, for example, all of the files for a video in HLS format or all of the files in the subscribers' area of a website.
- You don't want to change your current URLs.


## Developer Tool

Not in Dev or Arch exam:

Code Star:
way of project managing your code , CI tool chain , release withing minutes.
Code commit:
Source control , have git repositories,
Code Build:
compile and run tests agaistns it.
Code DEploy:
automates app deployment to EC2 instance and in premise instances as well aa to lambda as well.

Code Pipeline:
Its a CD service.
X-Ray:
Debug and Analysis services for serverless.


Cloud 9
IDE Environment, for writing your code.


Management Tools
Cloud watch - Most important, Monitoring service , bread and butter of sys ops.

Cloud Formation:
Very importatnt to work as solutions architect as well as for professional exam. Getting rid of physical servers etc  and turn your infrstructure to code.

Cloud Trail :
Anything you do inside AWS that triggers API and creates a log of it. so you need enable it for all the time.

AWS config:
Monitors config of AWS evironement for all the time. You can backward and forward time to visuali

Ops Work:
Elastic bean , uses chef and puppet. 	
