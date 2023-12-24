---
tags:
  - SageMaker
  - ml
  - deployment
source: https://docs.aws.amazon.com/sagemaker/latest/dg/deploy-model.html
date: 01/10/2023
---
### Summary

Amazon [[Servizi ML]] Inference is a fully managed service that enables you to deploy and manage machine learning (ML) models for real-time and batch inference. SageMaker Inference provides a broad selection of ML infrastructure and model deployment options to help you meet all your ML inference needs.

### Steps for deployment
For inference endpoints, the general workflow consists of the following:
- Create a model in SageMaker Inference by **pointing to model artifacts stored in Amazon S3 and a container image**.
- Select an inference **option**. For more information, see [Inference options](https://docs.aws.amazon.com/sagemaker/latest/dg/deploy-model.html#deploy-model-options).
- **Create** a SageMaker Inference **endpoint** configuration by choosing the instance type and number of instances you need behind the endpoint. You can use [Amazon SageMaker Inference Recommender](https://docs.aws.amazon.com/sagemaker/latest/dg/inference-recommender.html) to get recommendations for instance types. For Serverless Inference, you only need to provide the memory configuration you need based on your model size.
- Create a SageMaker Inference endpoint.
- Invoke your endpoint to receive an inference as a response.

### Inference options

SageMaker provides multiple inference options to fit your workload needs:
- **Real-time inference:** For **low latency or high throughput online inferences**, use a persistent and fully managed endpoint (REST API). Real-time inference can support payload sizes **up to 6 MB and processing times of 60 seconds**.
- **Serverless inference:** For **intermittent or unpredictable traffic patterns**, use serverless inference. SageMaker manages all of the underlying infrastructure, and you pay only for what you use. Serverless inference can support payload sizes up to **4 MB and processing times of 60 seconds**.
- **Batch transform:** For offline processing of large amounts of data, use batch transform. You can also use batch transform for pre-processing datasets. Batch transform **can support large datasets that are GBs in size and processing times of days**.
- **Asynchronous inference:** For queuing requests with large payloads and long processing times, use asynchronous inference. Asynchronous inference can support payloads up to 1 GB and processing times up to one hour. You can also scale down your endpoint to 0 when there are no requests to process.

### Related

- **Monitoring:** Monitor your model over time using [[Model Monitor]] to track model accuracy and drift. Set up alerts to be notified when there are deviations in your model’s quality. Monitor your endpoint’s health using Amazon CloudWatch metrics such as invocation errors and model latency.
- **CI/CD for model deployment:** Use [[SageMaker MLOps]] to automate the steps in your machine learning workflow and practice CI/CD. Use Model Registry to manage your model versions and the deployment and automation of your models.
- **Deployment guardrails:** Use deployment guardrails to update your model while it’s in production without impacting production. 
- **Optimize model performance:** Use SageMaker’s built-in algorithms and pre-built models, as well as prebuilt Docker images, which are developed for machine learning. Use SageMaker Neo to train TensorFlow, Apache MXNet, PyTorch, ONNX, and XGBoost models once and optimize them to deploy on ARM, Intel, and Nvidia processors.
- **Autoscaling:** Use autoscaling to dynamically adjust the number of instances provisioned in response to changes in your workload. If you have unpredictable traffic patterns or don’t want to set up scaling policies, you can also use Serverless Inference for an endpoint where SageMaker manages autoscaling for you.