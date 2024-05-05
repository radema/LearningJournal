---
tags:
  - aws
  - ml
date: 04/11/2023
---
| Instances / Service | Description | Link |
| --- | --- | --- |
| P3 | Addestramento su larga scala sensibile al fattore tempo. Provide high-performance computing with NVIDIA Tensor Core GPUs and up to 100 GB/s of network throughput for machine learning and HPC applications. The P3 instances **reduce** **machine learning training** times from days to minutes and increase the number of completed simulations for high-performance computing by 3-4 times. The instances are also optimized for distributed machine learning and HPC applications. The instances can be used with Amazon SageMaker. | https://aws.amazon.com/it/ec2/instance-types/p3/|
| inf1 | Riduzione Costi e miglioramento prestazioni. Instances for ML inference. These instances offer high-performance and low-cost ML inference, with up to 70% lower costs and up to 2.3 times higher effective transmission speeds compared to comparable Amazon EC2 instances.| https://aws.amazon.com/it/ec2/instance-types/inf1/ |
| G4 | Inferenza per i modelli che utilizzano le librerie NVIDIA CUDA, CuDNN o TensorRT. Le istanze G4 sono dotate di GPU NVIDIA T4 che offrono una velocità di trasmissione effettiva a bassa latenza fino a 40 volte migliore rispetto alle CPU. | https://aws.amazon.com/it/ec2/instance-types/g4/ |
| C5 | Inferenza per modelli che sfruttano le istruzioni per reti neurali vettoriali Intel AVX-512 (AVX512 VNNI). Le istanze C5 includono il supporto AVX-512 VNNI, che consente di velocizzare le tipiche operazioni di machine learning come la convoluzione e di migliorare automaticamente le prestazioni di inferenza su un'ampia gamma di carichi di lavoro di deep learning. | https://aws.amazon.com/it/ec2/instance-types/c5/ |
| F1 | use FPGA to allow the deployment of custom hardware accelerations. These instances are easy to program and include everything needed to develop, simulate, debug, and compile hardware acceleration code. They can be useful in many applications that require high bandwidth, advanced networks, and high processing power, such as genomics, research/analysis, image and video processing, network security, Electronic Design Automation (EDA), file and image compression, and Big Data analysis. | https://aws.amazon.com/it/ec2/instance-types/f1/ |
| Elastic Inference | non più disponibile per nuovi clienti. Amazon Elastic Inference consente di collegare le accelerazioni a basso costo basate su GPU alle istanze Amazon EC2 e SageMaker o alle attività Amazon ECS, così da ridurre i costi di esecuzione dell'inferenza di deep learning fino al 75% | https://aws.amazon.com/it/machine-learning/elastic-inference/ |
| [[Inferentia]] | accelerator designed by Amazon Web Services (AWS) to provide high-performance and cost-effective deep learning inference applications. | https://aws.amazon.com/it/machine-learning/inferentia/ |
| Neuron | AWS Neuron is an SDK that unlocks high-performance and cost-effective deep learning acceleration. It supports high-performance training on Amazon Elastic Compute Cloud (Amazon EC2) Trn1 instances | https://aws.amazon.com/it/machine-learning/neuron/ |
| [[IoT GreenGrass]] | AWS IoT Greengrass is a service that allows for local processing of AWS Lambda functions on IoT devices, reducing the cost of transmitting IoT data to the cloud. It also supports local container deployment, local device shadow functionality, local messaging, and access to local resources. AWS IoT Greengrass provides a modular solution with pre-integrated software components for common use cases, and a software catalog for additional components developed by the Greengrass community. It also offers remote management of device software and configuration, over-the-air updates, and integration with hardware security elements. AWS IoT Greengrass Secrets Manager allows for secure storage, access, rotation, and management of secrets at the edge, while AWS IoT Device Tester automates testing to ensure device compatibility with AWS IoT Greengrass | https://aws.amazon.com/it/greengrass/ |
