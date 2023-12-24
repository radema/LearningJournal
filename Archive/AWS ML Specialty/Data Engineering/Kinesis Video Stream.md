---
tags:
  - aws
  - kinesis
  - DataEngineering
date: 22/10/2023
---
a fully managed AWS service to #stream live video from devices to the AWS Cloud or build applications for #real-time video processing or batch-oriented video analytics.
# Benefits

- **Connect and stream from millions of devices**
- **Durably store, encrypt, and index data** – You can configure your Kinesis video stream to durably store media data for custom retention periods. Kinesis Video Streams also generates an index over the stored data based on producer-generated or service-side timestamps. Your applications can retrieve specified data in a stream using the time-index.
- **Serverless** 
- **Build real-time and batch applications on data streams** – You can use Kinesis Video Streams to build custom real-time applications that operate on live data streams, and create batch or one-time applications that operate on durably persisted data without strict latency requirements. 
- **Stream data more securely** – Kinesis Video Streams encrypts all data as it flows through the service and when it persists the data. Kinesis Video Streams enforces Transport Layer Security (TLS)-based encryption on data streaming from devices, and encrypts all data at rest using [[AWS KMS]] . Additionally, you can manage access to your data using AWS Identity and Access Management (IAM).