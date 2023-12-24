---
date: 21/10/2023
tags:
  - DataEngineering
  - aws
  - metadata
  - etl
---
The AWS Glue Data Catalog is a persistent technical [[metadata store]] in the AWS Cloud.

* Each AWS account has one AWS Glue Data Catalog per AWS Region. 
* Each Data Catalog is a highly scalable collection of tables organized into databases. A table is metadata representation of a collection of **structured** or **semi-structured data stored** in sources such as Amazon RDS, Apache Hadoop Distributed File System, Amazon OpenSearch Service, and others. 
* The AWS Glue Data Catalog provides a **uniform repository** where disparate systems can store and find metadata to keep track of data in data silos. You can then use the metadata to query and transform that data in a consistent manner across a wide variety of applications.

You use the Data Catalog together with AWS Identity and Access Management policies and Lake Formation to control access to the tables and databases. By doing this, you can allow different groups in your enterprise to safely publish data to the wider organization while protecting sensitive information in a highly granular fashion.

The Data Catalog, along with [[AWS CloudTrail]] and [[AWS Lake Formation]], also provides you with **comprehensive audit and governance capabilities**, with schema change tracking and data access controls. This helps ensure that data is not inappropriately modified or inadvertently shared.


