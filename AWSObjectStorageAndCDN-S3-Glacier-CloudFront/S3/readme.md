
# S3
---
### S3 - Simple Storage

Amazon S3 has a simple web services interface that you can use to store and retrieve
 - any amount of data, at any time, from anywhere on the web.

---

### S3
 - It gives any developer access to the same
 	- highly scalable,
 	- reliable,
 	- fast,
 	- inexpensive
   data storage infrastructure that Amazon uses to run its own global network of web sites.
 - The service aims to maximize benefits of scale and to pass those benefits on to developers.

---

###  S3 - Characterstics:
S3 is
- spread accross multiple devices and facilities
- Secure
- Object based storage
- File size can be 0 bytes to 5TB
- Unlimited Storage
- Files are stored in buckets


---

#### S3 Basics

	- S3 is object based stroage i.e it can store flat files.
	- Objects are files of different format e.g. Videos ,photos ,pdf that are called flat files.
	- S3 is place to store files.
	- Whereas block based storage we talk about databases.
	- S3 is unviversal names, i.e. bucket names must unique globally.(imp)
		- when you create a bucket , a new DNS address is created.
		- For example http://s3-eu-west-1.amazonaws.com/leanmentors ![alt text](https://github.com/khurramsyed/aws-training/blob/master/images/tip.jpeg "Important")
	- When you upload a file to S3 you will receive a 200 Status code if it was successful (imp)

---

### Data Consistency Model for S3

> ![alt Important](../../images/tip.jpeg)
If you write new object in S3 it is immediately updated  
and available this is clled **immediate consistency for PUTS**.

---

> ![alt text](../../images/tip.jpeg)
However you do not get that kind of speed with updates
(PUTS with existing data) and deletes (because of multi
 device and multi facility). It takes little bit of time.
 This is called **Eventual Consistency of Override for PUTS and DELETES**

---

> ![alt text](../../images/tip.jpeg "Important")
Updates are atomic, this means you get new or old data
but never corrupt/Intermediate data.

---

### S3 is simple Key Value Pair

	- S3 is object based, Objects consist of following:
		- Key (Name of the object) - File name
		- Value : Data consisting sequence of bytes
		- Version ID important for versioning (which version)
		- Metadata (Data about data e.g. file upload date)
		- Subresources exist underneath an object consits of:
			- ACL (Access control list) -Fine grained Permissions
				- Individual file level
				- bucket level
			- Torrent

---

### S3 - Basics

- S3 is:
	- Designed to be lexographical
	(sorts object in alpha order)

>![alt text](../../images/tip.jpeg "Important")
	    It is very important design consideration, for example  
	    you have log data and file names could be really really
		similar and files will be stored in same area and that
		can be performance bottleneck. If you add a salt for the
		file name at the start and make it different, it will be
		stored evenly across the S3, so we need to add randomness
		to filename.

----

### S3 - Basics

- S3 is build for 99.99% availability
- Amazon Guarantees 99.999999999% or 11 9s of S3
  durability (you wont loose a file)
- Tiered storage options
- Key value pair ,key being file name and value being the contents/bytes
- Tiered storage options
- Life cycle management (first 30 days S3, Next 30 day IA, and then RRS or Glacier for example)
- Versioning (one Object with multiple version)
- Encryption multiple encryptions techniques are possible.
- Secure using ACL or bucket policies.

---

### Storage Tiers

- S3 99.99% availability and 99.99999999% durability.
- S3-IA(Infrequenctly Access) for data that is less
  frequently accessed, but requires immediate access
  when needed and not hours, lower fee than
  S3 but there is retrieval fee.
- Reduced Redundancy Stroage (RRS) 99.99% availaibility but
  durability is down to 99.99%  of objects over a given year.
  (May be data that you can generate again)
- Glacier very cheap, used for archival but
  takes 5-5 hours to restore from glacier
  For Data Archival , very infrequncy access is need,
   First Byte latency is 3-5 hours.


---


S3 Charges
 -charged For
 	- Stroage - How mcuh data
  	- Requests - number of request being made to S3 objects
  	- Stoeage Mgmt pricing
  	- Data Transfer Pricing (coming into S3 is free, but replication)
  	- Transfer acceleration

>![alt text](../../images/tip.jpeg "Definition") Amazon S3 Transfer Acceleration enables fast, easy, and secure transfers of files over long distances between your client and an S3 bucket. Transfer Acceleration takes advantage of Amazon CloudFront’s globally distributed edge locations. As the data arrives at an edge location, data is routed to Amazon S3 over an optimized network path.


So My bucket location is in london , so if a user is uploading to bucket from Australia they can upload to Edge Location and

>![alt text](../../images/tip.jpeg "Very Imporant")
	- Object BAsed , no OS or Database (File, wor)
	- File Size 0B to 5TB
	- Files are stored in buckets
	- S3 has universal namespace
	- link for S3 follows pattern
		- https://s3-region.amazonaws.com/bucketname
		  for example
		 https://s3-eu-west-1.amazonaws.com/leanmentors
	- READ AFter Write consisetncy for PUTS of new Object
	- Eventual consisetncy for PUTS and Delete (Can take sometime to propagate)
	- Stroage Classes
		- S3 - Durable, Frequently Accessed, Immediately available
		- S3IA - Durable, Immediately Available, Infrequenct access , cheaper than above
		- S3 RRS (For data that is by nature easily reproducible e.g. Thumbnails)
		- Glacier - ARchival Data , waiting time 3-4 hours
	- Key
	- Value
	- VersionId
	- Meta Data
	- Subresources
		- Access Control List ACL
		- Torrent
	- Successful upload - Results in 200 hTTP Status
	- Only Object based
	- Must Read S3 FAQ before Exam.
