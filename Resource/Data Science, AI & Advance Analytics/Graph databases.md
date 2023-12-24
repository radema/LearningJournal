tags: #graphdb #graph #AnomalyDetection #ml [[Explainability]]


# References
[[20220222#^6356e5]]
[[20220222#^e45f2e]]

# Notes
From [Graph-based Anomaly Detection and Description: A Survey](https://arxiv.org/pdf/1404.4679.pdf) *by Leman Akoglu · Hanghang Tong · Danai Koutra (April 2014)*

> Detecting anomalies in data is a vital task, with numerous high-impact applications in areas such as security, finance, health care, and law enforcement. [...] As objects in graphs have long-range correlations, a suite of novel technology has been developed for anomaly detection in graph data.
>[...] In addition to revealing suspicious behavior, anomaly detection is vital for spotting rare events, such as rare disease outbreaks or side effects in medical domain with vital applications in the medical diagnosis.
>[...] data objects [...] may exhibit inter-dependencies which should be accounted for during the anomaly detection process.[...] Graphs provide a powerful machinery for effectively capturing these long-range correlations among inter-dependent data objects.

Four main reasons that make graph-based approaches to anomaly detection vital and necessary:
1. **Inter-dependent nature of the data**
2. **Powerful representation**
3. **Relational nature of problem domains**: *The nature of anomalies could exhibit themselves as relational. For example in the fraud domain, one could imagine two types of scenarios: (1) opportunistic fraud that spreads by word-of-mouth (if one commits fraud, it is likely that his/her acquaintances will also do so), and (2) organized fraud that takes place by the close collaboration of a related group of subjects.* 
4. **Robust machinery**: Finally, one could argue that graphs serve as more adversarially robust tools. [...] it would be harder for a fraudster to fit in to this network as good as possible without knowing its entire characteristic structure and dynamic operations.

## Definition of anomaly detection problem in a graph
> Given a (plain/attributed, static/dynamic) graph database, find the graph objects (nodes/edges/substructures) that are rare and that differ significantly from the majority of the reference objects in the graph.
> [...] an anomaly is treated as a data object or a group of objects that is rare, isolated (e.g., far-away points in n-dimensional spaces), and/or surprising (e.g., data instances that do not fit well in our mental/statistical model, or need too many bits to describe under the Minimum Description Length principle.

**Data Specific Challanges**
The challenges with respect to data are the same we face working with big data:
1. Scale and Dynamics
2. Complexity

**Problem Specific Challanges**
1. Lack and Noise of Labels
2. Class Imbalance and Asymmetric Error
3. Novel Anomalies
4. “Explaining-away” the Anomalies

### Anomaly Detection in Static Graphs
The main task is to spot anomalous network entities (e.g., nodes, edges, subgraphs) given the entire graph structure. 
It is possible to work with plain graphs or **attributed graphs**.

Approaches
1. **Feature-based**, extract structural graph-centric features that are sometimes used together with other features extracted from additional information sources for outlier detection in the constructed feature space. Essentially, these methods transform the graph anomaly detection problem to the well-known and understood outlier detection problem. ->* from a graph to structured "table" data* 
	>  **Graph-centric features**, compute various measures associated with the nodes, dyads, triads, egonets, communities, as well as the global graph structure 
	
	-> *Example*: egonet and related features
2. **Proximity-based**, exploit the graph structure to measure closeness (or proximity) of objects in the graph. These methods capture the simple autocorrelation between these objects, where close-by objects are considered to be likely to belong to the same class.
	-> example: PageRank
3. **Community-based**, rely on finding densely connected groups of “close-by” nodes in the graph and spot nodes and/or edges that have connections across communities. In fact, the definition of anomaly under this setting can be thought of as finding “bridge” nodes/edges that do not directly belong to one particular community.
4. **Structure-based**, identify substructures in the graph that are rare structurally, i.e. connectivity-wise, as well as attribute-wise. As such, inverse of frequent attributed subgraphs are sought out
5. **Relation learning-based**,  exploit the relationships between the objects to assign them into classes, where the number of classes is often two: anomalous and normal.

---

### Anomalies in dynamic graphs

> Given a sequence of (plain or attributed) graphs, find (i) the timestamps that correspond to a change or event, as well as (ii) the top-k nodes, edges, or parts of the graphs that contribute most to the change (attribution).

Approaches:
1. **Feature-based**, the general approach in detecting anomalous timestamps in the evolution of dynamic graphs can be summarized as extract summary, compare consecutive graphs and select based on distance or threshold
2. **Decomposition-based**, detect temporal anomalies by resorting to matrix or tensor decomposition of the time-evolving graphs, and interpreting appropriately selected eigenvectors, eigenvalues or singular values.
3. **Community-based**, monitor graph communities or clusters over time and report an event when there is structural or contextual change in any of them.
4. **Window-based**,  methods that are bound to a time window in order to spot anomalous patterns and behaviors in the input graph sequence.


### Interpretability
> Given a set of anomalies of graph entities (nodes and edges) interpret and explain the detection of the individual anomalies, find and characterize the associations among the anomalies.

Two possible approaches:
- **Individual** interpretations
- **Global** interpretations

### Use cases
- subscription fraud <- the fraudster often acquires an account using false identity with the intention of using the service for free and not making any payments.
- action frauds <- e fraudsters’ behavior reveals that in order to game the feedback and reputation system, fraudster create additional accounts or “roles” called accomplices. Accomplices and fraudster do not necessarily interact among each other. Moreover, honest users trade among themselves as well as with accomplices that also look like honest users. 
- accounting fraud <- spotting high-risk accounts with suspicious transactions behavior
- security networks <- spot securities brokers that are likely to commit fraud and other violations of securities regulations in the future
- computer networks <- the nodes represent the agents in the networks, such as ad/file/directory servers and client nodes, and edges represent their communications over the network (note that the edges may be weighted, capturing volume or frequency). The insight behind tracking the dynamic nature of the network graph is the assumption that the communication behavior of a compute node would change when under attack.


--- 

![[20220303#^f9d463]]

-   [**Part 1: Exploring Connected Fraud Data**](https://neo4j.com/developer-blog/exploring-fraud-detection-neo4j-graph-data-science-part-1/)
-   [**Part 2: Resolving Fraud Communities Using Entity Resolution & Community Detection**](https://neo4j.com/developer-blog/exploring-fraud-detection-neo4j-graph-data-science-part-2/) -> Community based approach
-   [**Part 3: Recommending Suspicious Accounts With Centrality & Node Similarity**](https://neo4j.com/developer-blog/exploring-fraud-detection-neo4j-graph-data-science-part-3/) -> Proximity based approach
-   [**Part 4: Predicting Fraud Risk Accounts With Machine Learning**](https://neo4j.com/developer-blog/exploring-fraud-detection-neo4j-graph-data-science-part-4/)

#### Part 1 -  Exploring Connected Fraud Data
Dataset introduction - rteal-world peer-to-peer (P2P) platform. 
Entities: User, Device, Card, IP.
Relationships: 
- User -> P2P -> User
- User -> Referred -> User
- User -> Used -> Device
- User -> HAS_CC-> Card
- User -> HAS_IP -> IP

> Each user node has an indicator variable for money transfer fraud (named `MoneyTransferFraud`) that is 1 for known fraud and 0 otherwise. This indicator is determined by a combination of credit card chargeback events and manual review. A chargeback is an action taken by a bank to reverse electronic payments. It involves reversing a payment and triggering a dispute resolution process, often for billing errors and unauthorized credit use. In short, a user must have at least one chargeback to be considered fraudulent. Only a small proportion of the user accounts, roughly 0.7 percent, are flagged for fraud.

> ... the fraud activity is not completely labeled given the lack of connectivity and the limited chargeback logic used to flag fraud.

In a graph, we can attempt to roughly identify these fragmented identities with **[[Community Detection]]**, a large set of methods that attempt to partition graphs into well connected groups, a.k.a. Communities, where the connectivity in the communities is significantly higher than outside the community. There are multiple forms of community detection.
- **Louvain CD**: it uses a form of modularity scoring to split up the graph into hierarchical clusters.

#### Part 2 -  Resolving Fraud Communities Using Entity Resolution & Community Detection

More formal definitions for resolving entities that will allow to partition well-defined communities in a scalable manner.
Definition of Entity Resolution (ER) rules that will allow to draw relationshipts between users which belong to the same underlying community. Then, it is is applied the Weakly Connected Components (WCC) algorithmto resolve the communities and all users in communities which include fraudsters are labelled with a fraud risk attribute.

1. ER -> define business rules to create a relationship between two nodes (for example two users)
2. Use Weakly Connected Components is a scalable community detection algoritmic. It is deterministic and explainable. Detect communities based on set of relationships
3. Flag communities with at least one fraudster

#### Part 3 - Recommending Suspicious Accounts With Centrality & Node Similarity

Expand beyond our business logic to automatically identify other users that are suspiciously similar to the fraud risks already identified.

- User Weighted Degree Centrality to recommend potential high risk accounts over the whole graph -> global method
- Apply similarity algorithms to score and recommend users similar to specific instances -> local method
- Node **similarity** parallelizes well and is **explainable**. It identifies pairs of similar nodes based on a straightforward Jaccard similarity calculation. Alternatives:  FastRP + KNN

#### Part 4 - Predicting Fraud Risk Accounts With Machine Learning
There are multiple reasons why we may want to add supervised machine learning to predict the additional fraud risks:
1.  **Proactive Detection:** We can train a model to identify fraudulent actors ahead of time (such as before additional chargebacks or system flags) and better identify new communities that aren’t connected to older known fraud accounts.
2.  **Measurable Performance:** Supervised learning models produce clear performance metrics that enable us to evaluate and adjust as needed.
3.  **Automation:** Supervised machine learning automates the prediction of fraud risk accounts.

**Building features**:
- Community Indicator and Size
- [[PageRank]] on P2P With Shared Card Degree
- Degree Centrality on the Shared Id Rule
- P2P weighted Degree Centrality and PageRank
- Degree Centrality for Cards, Devices, and IPs

Then apply ML in python (or RapidMiner)