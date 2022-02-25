tags:
- #graphdb 
- #graph 
- #AnomalyDetection


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

### Anomaly Detection in Statis Graphs
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