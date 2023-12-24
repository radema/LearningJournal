---
tags:
  - kinesis
  - aws
  - DataEngineering
  - stream
source: https://aws.amazon.com/it/kinesis/data-streams/features/?nc=sn&loc=2
---
https://aws.amazon.com/it/kinesis/data-streams/getting-started/?nc=sn&loc=4

https://docs.aws.amazon.com/streams/latest/dev/introduction.html

Amazon Kinesis Data Streams is a massively **scalable**, **durable**, and **low-cost streaming data service**. 

### Features

- **Serverless**: no servers to manage. The on-demand mode removed the provision need or manage automatically scaling capacity. 
- **Highly available and durable**
- **Low latency** : make data available within 70 milliseconds
- **Dedicated throughput per consumer**: up to 20 consumers for data stream
- **Choose between on-demand and provisioned capacity mode**

Integrated with several AWS services, like::
* [[Kinesis Firehose]] for near-real time transformation and delivery to [[S3]]
* [[Kinesis Data Analytics]], or Amazon Managed Service for Apache Flink for managed stream processing
* [[AWS Lambda]] for event or record processing
* [[AWS PrivateLink]] for private connectivity
* [[AWS Cloudwatch]] for metrics and log processing
* [[AWS KMS]] for server-side encryption

### Key concepts

* **data producer**: application which emits records as they are generated. The producers assign partition keys to records
* **data consumer**: Kinesis application or AWS service retrieving data from all shards in a stream as it is generted. 
* **data stream**: is a logical grouping of shards. By default, retain data for 24 hours by default, up to 365 days
* **shard**: base throughput unit of an Amazon kinesis data stream
	* append-only log containing an ordered sequence of records by arrival time
	* can **ingest** up to 1k data per second, i.e. **1MB/sec**, in **input**
	* **2MB/sec output** for each data consumer 