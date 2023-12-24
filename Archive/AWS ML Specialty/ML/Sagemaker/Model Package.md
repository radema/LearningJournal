---
tags:
  - SageMaker
  - aws
  - deployment
  - ml
date: 01/10/2023
source: https://docs.aws.amazon.com/sagemaker/latest/dg/sagemaker-mkt-create-model-package.html
---

To create a model package resource that you can use to create deployable models in Amazon [[Servizi ML]] and publish on AWS Marketplace:

- **Docker container** that contains the **inference code**, or the algorithm resource that was used to train the model.
- The **location** of the model **artifacts**. Model artifacts can either be packaged in the same Docker container as the inference code or stored in Amazon [[S3]].
- The **instance types** that your model package supports for both real-time inference and batch transform jobs.
- **Validation profiles**, which are **batch transform jobs** that [[Servizi ML]] runs to test your model package's inference code.

You can list products on AWS Marketplace only if validation succeeds.
1. Create a model in your account using the model package's inference image and the optional model artifacts that are stored in Amazon [[S3]].
2. Create a transform job in your account using the model to verify that your inference image works with [[Servizi ML]].
3. Create a validation profile. (In your validation profile, provide only data that you want to expose publicly.)