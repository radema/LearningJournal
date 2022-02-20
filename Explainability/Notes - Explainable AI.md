#explaibility  #Intelligibility #Explanations #ExplainableAI #Decisionmaking
# Designing Theory-Driven User-Centric Explainable AI

Set of tecniques to help humans explain AI/ML models prediction. 

Explanations are needed when i) it is observed a deviation from the expected result or ii) users wants to monitor an event.

The main reasons that people want explanations is to facilitate learning by allowing the user to: 
(i) find a small set of causes to simplify their observation, 
(ii) generalize these observations into a conceptual model or a pattern where they can predict and control future phenomena.

Explaination tasks:
- transparency
- support decision making
- scrutability and debugging
- moderate trust

## XAI techniques to generate explaination

We characterize AI and XAI techniques by
- support human reasoning and specific methods of scientific inquiry, such as Bayesian probability, similarity modeling, and queries;
- how to represent explanations with visualization methods, data structures and atomic elements.

### Bayesian probability
	Due to the stochastic nature of events, reasoning with probability and statistics is important in decision making. Understanding outcome probabilities can inform users about the expected utility. Useful to know how influential a factor or feature is to a decision outcome.

### Similarity Modeling
	As people learn general concepts, they seek to group similar objects and identify distinguishing features to differentiate between objects.
	Many methods are data-driven to match candidate objects with previously seen data (training set).
	Identifying causal attributions can then help users ascertain the potential causes for the matching and grouping. 
	Note that while rules appear to be a distinct explanation type, we consider them descriptions of the boundary conditions between dissimilar groups.

### Intelligibility queries
	Starting from a usability-centric perspective, the authors developed a suite of colloquial questions about the system state (Inputs, What Output, What Else Outputs, Certainty), and inference mechanism (Why, Why Not, What If, How To). While they initially found that Why and Why Not explanations were most effective in promoting system understanding and trust.

### XAI Elements
	We identify building blocks that compose many XAI explanations.
	Some examples: feature attribution or influence, similar (or different) instances from the training data, `name` and `value` of input or outputs and the `clause` to describe if the value of a feature is above or below a threshold prototypes, criticism, and counter-examples.
		   
### Data Structures
	The simplest and most common way to construct explanations is as `lists`. Lists are oft en used to represent input feature att ributions, and can also represent output class attributions.
	Logical clauses can be combined into rules or as a decision tree to describe branching logic. For more complicated structures, it is possible to use graphs. 

### Visualizations
	      To provide data and algorithmic transparency, basic charts can be used to represent raw data and canonical visualizations can be used to illustrate model structure. To support causal attribution, tornado diagrams of vertical bar charts are popularly used for lists of attributions.
		  These visualization techniques support contrastive explanations and counterfactual reasoning by allowing for the comparison of different attributions or understanding of relationships between factors.
		  Sensitivity analysis provides several methods as a robustness test to ask what if the input factors change slightly or are perturbed, whether the outcome of a decision will change.

## XAI techniques to support reasoning

### Mitigate Representativeness Bias      
	Representativeness bias happens when a decision maker perceives the current situation as similarto other cases of a wrong classification.
	To mitigate this bias, we can show prototype instances to represent different outcomes; the prototypes can be rank-ordered by their similarity to the current case or by explicitly showing a (dis)similarity distance metric. 
	To allow for comparison between cases by inspecting features, the difference in value or attribution per feature can be shown to contrast the differences between cases.
	
### Mitigate Availability Bias
	Availability bias can occur when decision makers are unfamiliar with how often a particular outcome happens. 
	This can be mitigated by showing the base rate of the outcome (prior probability ) based on frequencies in the training dataset, SHAP bias.
	
### Mitigate Anchoring Bias
	The anchoring bias occurs when the decision maker forms a skewed perception.
	This can be facilitated by showing input attributions for multiple outcomes. Lighthall et al. also proposed using Klein’s premortem prospective hindsight exercise, where decision makers posit that their primary hypothesis ends up being wrong and have to determine why. 
	This can be facilitated by generating a counterfactual  explanation with rules (e.g., Anchor LIME or LORE) to determine what input features could be slightly diff erent to lead to a different outcomes. 
	Alternatively, sensitivity analysis  could be used to simulate a range of perturbed input values and test the stability of the primary hypothesis.
### Mitigate Confirmation Bias
	Reason with the hypothetico-deductive method. Show findinds (Input attribution) instead of posterior probability or class attribution. 
### Moderate Trust
	To moderate users to trust the system at appropriate times or trust specific sub-components of the system. The system should be transparent  to show What and Inputs explanations and show its classification certainty. Once the user detects erroneous reasoning in the system, scrutability  features can be contrasted  to allow for model debugging and correction (by a technical expert).
	
## XAI Framework
- Consider user's reasoning goals and biases
- identify explanations which help reasoning or reduce bias
- integrate these facilities

### Further recommendations
- Support Hypothesis generation
- Support forward (data-driven) reasoning
- Support Coherent Factors
- Support access to situational and source data
- Support bayesian reasoning
- Integrate multiple explanations


## References
- Danding Wang, Qian Yang, Ashraf Abdul, Brian Y. Lim. 2019. Designing Theory-Driven User-Centric Explainable AI. In 2019 CHI Conference on Human Factors in Computing Systems Proceedings (CHI 2019), May 4–9