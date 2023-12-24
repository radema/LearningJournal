---
tags:
  - aws
  - SageMaker
  - ml
date: 18/11/2023
---
SageMaker provides image processing algorithms that are used for image classification, object detection, and computer vision.

- [Image Classification - MXNet](https://docs.aws.amazon.com/sagemaker/latest/dg/image-classification.html)—uses example data with answers (referred to as a _supervised algorithm_). Use this algorithm to **classify images.**
- [Image Classification - TensorFlow](https://docs.aws.amazon.com/sagemaker/latest/dg/image-classification-tensorflow.html)—uses pretrained **TensorFlow Hub models to fine-tune** for specific tasks (referred to as a _supervised algorithm_). Use this algorithm to classify images.
- [Object Detection - MXNet](https://docs.aws.amazon.com/sagemaker/latest/dg/object-detection.html)—**detects and classifies objects in images** using a single deep neural network. It is a supervised learning algorithm that takes images as input and identifies all instances of objects within the image scene.
- [Object Detection - TensorFlow](https://docs.aws.amazon.com/sagemaker/latest/dg/object-detection-tensorflow.html)—**detects bounding boxes and object labels** in an image. It is a supervised learning algorithm that supports transfer learning with available pretrained **TensorFlow** models.
- [Semantic Segmentation Algorithm](https://docs.aws.amazon.com/sagemaker/latest/dg/semantic-segmentation.html)—provides a fine-grained, pixel-level approach to developing computer vision applications.



|Algorithm name|Channel name|Training input mode|File type|Instance class|Parallelizable|
|---|---|---|---|---|---|
|Image Classification - MXNet|train and validation, (optionally) train_lst, validation_lst, and model|File or Pipe|recordIO or image files (.jpg or .png)|GPU|Yes|
|Image Classification - TensorFlow|training and validation|File|image files (.jpg, .jpeg, or .png)|**CPU or GPU**|Yes (only across multiple GPUs on a single instance)|
|Object Detection|train and validation, (optionally) train_annotation, validation_annotation, and model|File or Pipe|recordIO or image files (.jpg or .png)|GPU|Yes|
|Object Detection - TensorFlow|training and validation|File|image files (.jpg, .jpeg, or .png)|GPU|Yes (only across multiple GPUs on a single instance)|
|Semantic Segmentation|train and validation, train_annotation, validation_annotation, and (optionally) label_map and model|File or Pipe|Image files|GPU (single instance only)|**No**|