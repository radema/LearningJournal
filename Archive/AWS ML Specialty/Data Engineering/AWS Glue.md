---
date: 21/10/2023
tags:
  - aws
  - DataEngineering
  - etl
---
### Intro

AWS Glue is a **scalable**, **serverless** [[data integration]] service that makes it easy to discover, prepare, and combine data for analytics, machine learning, and application development.

* Connect to more than 70 diverse data sources and manage your data in a centralized [[Data Catalog]]. 
* Create, run, and monitor extract, transform, and load **(ETL) pipelines** to load data into your data lakes.

### Features

- **Discovery:** Discover and organize data
	- **Unify and search across multiple data stores** – Store, index, and search across multiple data sources and sinks by cataloging all your data in AWS.
	- **Automatically discover data** – Use [[AWS Glue crawlers]] to automatically infer schema information and integrate it into your [[AWS Glue Data Catalog]].
	- **Manage schemas and permissions** – Validate and control access to your databases and tables.
	- **Connect to a wide variety of data sources** – Tap into multiple data sources, both on premises and on AWS, using AWS Glue connections to build your data lake.
- **Development:** Transform, prepare, and clean data for analysis
	- **Visually transform data with a drag-and-drop interface**
	- Build complex ETL pipelines with simple **job scheduling**
	- Clean and transform **streaming data in transit**
	- **Deduplicate and cleanse data with built-in machine learning**: Clean and prepare your data for analysis without becoming a machine learning expert by using the `FindMatches` feature. This feature deduplicates and finds records that are imperfect matches for each other.
	- Built-in job notebooks
	- Edit, debug, and test ETL code
	- **Define, detect, and remediate sensitive data**: AWS Glue sensitive data detection lets you define, identify, and process sensitive data in your data pipeline and in your data lake
- **Operations:** Build and monitor data pipelines
	- **Automatically scale based on workload**
	- **Automate jobs with event-based triggers**
	- **Run and monitor jobs** – Run AWS Glue jobs with your choice of engine, Spark or Ray. Monitor them with automated monitoring tools, AWS Glue job run insights, and AWS CloudTrail. Improve your monitoring of Spark-backed jobs with the Apache Spark UI.
	- **Define workflows for ETL and integration activities**

### New Compenent

The [[AWS Glue Schema Registry]] is a new feature that allows you to centrally discover, control, and evolve **data stream** schemas. A _schema_ defines the structure and format of a data record. With AWS Glue Schema Registry, you can manage and enforce schemas on your data streaming applications.

Supported format:
* `avro`
* `json`
* `protobuf`

[[AWS Glue Data Quality]] allows you to measure and monitor the quality of your data so that you can make good business decisions. Built on top of the open-source DeeQu framework, AWS Glue Data Quality provides a managed, serverless experience. AWS Glue Data Quality works with Data Quality Definition Language (DQDL), which is a domain specific language that you use to define data quality rules.


### Security

#### Data Protection

* **Encryption at rest**: configure ETL jobs and development endpoints to use [[AWS KMS]] to encrypt data at rest. Additionally, you can use it to encrypt job bookmarks and the logs generated by [crawlers](https://docs.aws.amazon.com/glue/latest/dg/add-crawler.html) and ETL jobs. Also metadata can be encrypted. 
* **Encryption in transit:** Transport Layer Security (TLS) encryption for data in motion. You can configure encryption settings for crawlers, ETL jobs, and development endpoints using [security configurations](https://docs.aws.amazon.com/glue/latest/dg/console-security-configurations.html) in AWS Glue. You can turn on AWS Glue Data Catalog encryption via the settings for the Data Catalog.
* **FIPS compliance:** If you require FIPS 140-2 validated cryptographic modules, a FIPS endpoint
* **Key Management** 
* **AWS Glue dependency:** [[AWS Cloudwatch]] for logs, [[AWS CloudFormation]] to work with stacks, IAM, EC2, S3, Redshift, RDS
* **Development endpoints:** development endpoint is an environment that you can use to develop and test your AWS Glue scripts
#### IAM
#### Infrastructure
* You can establish a private connection between your VPC and AWS Glue by creating an _interface VPC endpoint_. Interface endpoints are powered by [[AWS PrivateLink]], a technology that enables you to privately access AWS Glue APIs **without an internet gateway, NAT device, VPN connection, or AWS Direct Connect connection**.