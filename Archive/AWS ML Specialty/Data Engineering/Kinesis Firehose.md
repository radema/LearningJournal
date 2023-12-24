---
tags:
  - kinesis
  - DataEngineering
  - aws
  - stream
source: https://aws.amazon.com/it/kinesis/data-firehose/features/?nc=sn&loc=2
---
https://docs.aws.amazon.com/firehose/latest/dev/what-is-this-service.html

Service lo load streaming data into data stores and analytics tools. 
Fully **managed** service to capture, transform and load streaming data into [[S3]], [[Amazon Redshift]], etc.

### Using interface VPC endpoints (AWS PrivateLink) for Kinesis Data Firehose

To get started, create an interface VPC endpoint in order for your Kinesis Data Firehose traffic from your Amazon VPC resources to start flowing through the interface VPC endpoint. When you create an endpoint, you can attach an endpoint policy to it that controls access to Kinesis Data Firehose. 