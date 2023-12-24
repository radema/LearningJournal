---
date: 15/10/2023
source: https://aws.amazon.com/it/products/security/
---

Specific topics to be reviewed:
* VPC endpoint
* security with AWS
* ACL


* **IAM** : centrilized management defined respect on the following criteria: who, what, how. This is down through identity roles and policies. It can be supported by  [[Amazon Cognito]]; using it, it is possible to add features like sign-up and sign-in for users and controll access to all applications. Cognito provide an identity archive which is **scalable** and can be federated with the company. 
* **Monitoring**: AWS provides several services which can be used to monitor access and usage to the different services:
	* [[Amazon GuardDuty]]: a threath detection service that continuosly monitors for compromised accounts, anomalous behavior and malware. It can monitor continuosly resources and workloads for potential threads. It also can be integrated with AWS Lambda for automated remediation or prevention. Based on machine learning
	* [[Amazon Inspector]]: an automated security vulnerability management service that continually evaluates your resources for **software** vulnerabilities and unintended network exposure. 
	* [[Amazon Detective]]: investigate potential security issues
	* [[AWS Config]]: records and normalizes the changes into a consistent format for changes in **configuration** which occur in your AWS resources. AWS Config automatically evaluates the recorded configurations against the configuration that you specify. 
	* [[AWS Cloudwatch]]: complete visibility into your cloud resources and applications. It collect **metrics** and **logs** from your resources, applications and services that run on AWS or on-premises servers. Monitor and visualize applications and infrastructure with dashboards, troubleshoot with correlated logs and metrics and set alerts. It also allow to automate response to operational changes using CloudWatch Events and autoscaling. 
	* [[AWS CloudTrail]]: it record **user activities** and **API** usage in AWS services. All events are delivered to S3 and Amazon CloudWatch Logs. Data can be monitored with [[CloudTrail Insights]] or [[Amazon EventBridge]]. Data can be then analyzed in AWS CloudTrail or in [[Amazon Athena]]
* **Networking**:
	* [[AWS Firewall Manager]]: Centralized Firewall management to control the access rules for all accounts and applications in AWS organizations. 
	* [[AWS Shield]]: managed DDoS protection.
	* [[AWS WAF]]: protect your web application from common web exploits by setting policies, blocking and filtering access and then monitoring data using [[Amazon CloudWatch]] and take acton based on [[Amazon Kinesis Data Firehose]]
	* [[Route 53 Resolver]]: service to distribute the DNS protection in all the VPC. The Route allows to block the query towards risky domains. 
* Data Protection
	* [[Amazon Macie]]: ML-based service to identify sensitive data and protect them in AWS. Send result to [[Amazon EventBridge]] and AWS Security Hub for automated remediation and workflow integration
	* [[AWS KMS]]: Key Management System which allows to create, manage and control keys and cryptography between applications and services. 
	* [[AWS CloudHSM]]: services to apply the provisioning and management of security modules for single-tenant hardware
	* [[Gestione certificati]]
	* [[Crittografia di pagamento]]
	* [[AWS Secrets Manager]]: archives credentials, API keys, token and other secrets for other services like AWS Lambda. 