---
date: 21/10/2023
tags:
  - aws
  - DataEngineering
  - etl
---
You can use a crawler to populate the [[AWS Glue Data Catalog]] with tables.  A crawler can crawl multiple data stores in a single run. Upon completion, the crawler creates or updates one or more tables in your Data Catalog. 
The ETL job reads from and writes to the data stores that are specified in the source and target Data Catalog tables.

When a crawler runs, it takes the following actions:
- **Classifies data to determine the format, schema, and associated properties of the raw data** – You can configure the results of classification by creating a custom classifier.
- **Groups data into tables or partitions** – Data is grouped based on crawler heuristics.
- **Writes metadata to the Data Catalog** – You can configure how the crawler adds, updates, and deletes tables and partitions.

1. you choose one or more classifiers that evaluate the format of your data to infer a schema. 
2. the first classifier in your list to successfully recognize your data store is used to create a schema for your table. 
3. You can use built-in classifiers or define your own.

To configure the crawler, you define:
* basic crawler properties like name and description
* data sources to be scanned and classifiers
* security settings (IAM and encryption properties)
* output e scheduling
* 