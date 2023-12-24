Amazon SageMaker Feature Store is a tool that makes it easy to create, share, and manage features for machine learning development. 
It reduces repetitive data processing and curation work required to convert raw data into features for training an ML algorithm. 
Feature Store is a centralized store for features and associated metadata so features can be easily discovered and reused. 
You can create an **online** or an **offline** store. 
* The online store is used for low latency real-time inference use cases 
* the offline store is used for training and batch inference. Feature groups are mutable and can evolve their schema after creation. 

Feature Store is distributed across multiple Availability Zones (AZs) for resilience