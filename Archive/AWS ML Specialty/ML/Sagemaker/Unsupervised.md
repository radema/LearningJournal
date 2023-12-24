---
tags:
  - aws
  - SageMaker
  - unsupervised
date: 18/11/2023
---
|Algorithm name|Channel name|Training input mode|File type|Instance class|Parallelizable|
|---|---|---|---|---|---|
|IP Insights|train and (optionally) validation|**File**|CSV|**CPU** or GPU|Yes|
|K-Means|train and (optionally) test|File or Pipe|recordIO-protobuf or CSV|CPU or GPUCommon (**single GPU device on one or more instances)**|**No**|
|PCA|train and (optionally) test|File or Pipe|recordIO-protobuf or CSV|GPU or CPU|Yes|
|Random Cut Forest|train and (optionally) test|File or Pipe|recordIO-protobuf or CSV|**CPU**|Yes|

