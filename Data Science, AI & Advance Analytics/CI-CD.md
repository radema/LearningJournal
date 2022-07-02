#DataScience 

# References and Ideas
1. [How to Automate Data Analytics Using CI/CD](https://medium.com/gooddata-developers/how-to-automate-data-analytics-using-ci-cd-9f1475065d61), by Patrik Braborec on Medium
2. [https://resources.github.com/devops/tools/automation/actions/?utm_source=pocket_mylist](What is GitHub Actions? How automation & CI/CD work on GitHub), on GitHub Resources website

---

### How to Automate Data Analytics Using CI/CD
Automatization made using:
* [[Dagger]]: test pipeline locally and push to pipeline vendors like Gitlab or Github
* [[Gitlab]]
* [[GoodData]]: create metrics and dashboards which can be accessed using the python SDK. Based also on a Logical Data Model. 

### What is GitHub Actions?
* capabilities for automation and CI/CD
* Hosted VMs and docker support
* all automations are handled via YAML files placed under the .github/workflows directory
* free and available for use on any public repository and self-hosted runner
* limit of 500MB of workflows and execute 2k minutes of tasks per month

**Popular use cases**
* Build, test and deploy (CI/CD)
* Automate repetitive tasks
* Manage users easily at scale
* Easily add preferred tools and services to your project
* Review and test code
* tracking of your projects