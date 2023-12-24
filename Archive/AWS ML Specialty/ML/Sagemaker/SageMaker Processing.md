SageMaker Processing is a tool that allows users to analyze data and evaluate machine learning models on Amazon SageMaker. 
It provides a simplified, managed experience for running data processing workloads such as 
* feature engineering, 
* data validation, 
* model evaluation, 
* and model interpretation. 


Users can use the Amazon SageMaker Processing APIs during the **experimentation phase** **and after the code is deployed** in production to evaluate performance. 
The underlying infrastructure for a Processing job is fully managed by Amazon SageMaker, and cluster resources are provisioned for the duration of the job and cleaned up when the job completes.
The output of the Processing job is stored in the Amazon S3 bucket specified by the user. 
Input data must be 
* stored in an Amazon S3 bucket, 
* Amazon Athena or Amazon Redshift can also be used as input sources. 

Amazon SageMaker Processing provides sample Jupyter notebooks that show how to perform data preprocessing, model evaluation, or both. Users can monitor Amazon SageMaker Processing jobs with [[CloudWatch]] logs and metrics