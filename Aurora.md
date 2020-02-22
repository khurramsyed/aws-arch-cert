# Amazon Aurora

Amazon Aurora is a `MySQL and PostgreSQL-compatible` relational database built for the cloud, that combines the performance and availability of traditional enterprise databases with the `simplicity` and `cost-effectiveness` of open source databases.

### Benefits
- Amazon Aurora is up to `five times faster than standard MySQL databases` and `three times faster than standard PostgreSQL` databases
- It provides the security, availability, and reliability of commercial databases at `1/10th the cost`.
-Amazon Aurora is `fully managed by Amazon Relational Database Service (RDS)`, which automates time-consuming administration tasks like hardware provisioning, database setup, patching, and backups.


- You no longer need to worry about database management tasks such as hardware provisioning, software patching, setup, configuration, or backups

### Aurora V MySQL
![alt Aurora v mySQL](AuroraVMySQL.png)

### Aurora Cluster

| Auroa Cluster |
| :------------- |
| ![alt Aurora Cluster](AuroraCluster.png)      |
| Auroa maintains 6 copies of database across 3 AZ (2 in Each Zone  )|

- Each Aurora DB cluster can have up to 15 Aurora Replicas in addition to the primary DB instance.


### High Availability and Replication

- Amazon Aurora automatically divides your database volume into 10GB segments spread across many disks. Each 10GB chunk of your database volume is replicated six ways, across three Availability Zones. (As Shown above)
- Amazon Aurora is designed to transparently handle the `loss of up to two copies of data without affecting database write availability` and up to `three copies without affecting read availability`.
-  Amazon Aurora storage is also `self-healing`. Data blocks and disks are continuously scanned for errors and repaired automatically.




### Aurora Reader Endpoints (Load Balancing)

A reader endpoint for an Aurora DB cluster provides load-balancing support for read-only connections to the DB cluster. Use the reader endpoint for read operations, such as queries. By processing those statements on the read-only Aurora Replicas, this endpoint reduces the overhead on the primary instance. It also helps the cluster to scale the capacity to handle simultaneous SELECT queries, proportional to the number of Aurora Replicas in the cluster. Each Aurora DB cluster has one reader endpoint.

If the cluster contains one or more Aurora Replicas, the reader endpoint load-balances each connection request among the Aurora Replicas. In that case, you can only perform read-only   statements such as SELECT in that session. If the cluster only contains a primary instance and no Aurora Replicas, the reader endpoint connects to the primary instance. In that case, you can perform write operations through the endpoint.


### [AURORA FAQs](https://aws.amazon.com/rds/aurora/faqs/?nc=sn&loc=6ss)
