#ml 

Author: Chip Huyen

# Machine Learning Systems
ML is a mathematical approach which can be used to **learn complex pattern from data and make predictions on unseen data**.
This means that ML can be adopted if our problems has the following characteristics:
* **Learn**, i.e. the system has the capacity to learn (otherwise you cannot start)
*  **Complex**, patterns are complex (otherwise use other approaches)
* **Patterns**, there is something to learn (otherwise it is just random guess)
* **Existing data**, data are available or it is possible to collect them
* **Unseen data** which shares patterns with the training data 

Other hints which encourage ML usage:
* **ripetition**
*  **scale**
*  **changing patterns**
Some important use cases:
1. Search engines
2. Recommendation systems
3. Fraud Detection
4. price optimization
5. forecasting customer demand
6. reducing customer acquisistion costs
7. churn prediction
8. automated support ticket classification

## Drift for ML in business context

*Objectives* are different, based on the several stakeholders.
*Computational priority* focus on fast inference and low latency. *Data* are constantly shifting. *Fairness and interpretability* are important, if not necessary. 

Systems design is the process of defining all the components of a system:
*  interface, 
*  algorithms, 
*  data,
*  infrastructure,
*  hardware

These elements must be discussed when you design a system, produce a draft for an rfp, etc. All the elements must be decide after a **requirements analysis phase**.
The requirements can be declined following four directions:
* reliability -> ability of the system to work at the desired level of performance in any case of incidents (hardware/software faults, human errors, etc.)
* scalability -> ability of the system to work at the desired level of performance as the system grows (in volume, traffic, velocity, complexity, etc.)
* maintainability -> system easy to maintain for different contributors
* adaptability -> ability of the system to detect drift and changes in data without service interruption

The project would follows these phases:
1. Project Scoping: laying out goals & objectives, constrints and evaluation criteris. Stakeholders should be identifies and involved. Resources should be estimated and allocated. 
2. Data engineering -> create training data
3. ML model development -> label data, generate features, train and optimize models, evaluation, etc.
4. Deployment -> make models accessible to users. 
5. Monitoring and continual learning -> monitor performance decay and maintainance to adapt to chaging data and requirements
6. Business anaysis -> All systems have to be evaluated from a business perspective. 