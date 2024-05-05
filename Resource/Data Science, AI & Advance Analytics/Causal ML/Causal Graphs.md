---
tags:
  - causality
  - AI
  - DataScience
  - ml
---

# Causal Graphs and Data Science

## Intro

L'obiettivo di queste note non è quello di fornire un tutorial o un riassunto teorico riguardo sui temi di causal inference o causal analysis. L'obiettivo principale è di raccogliere tutte le analisi , approfondimenti e ragionamenti personali al riguardo. Queste note vogliono essere una sorta di "deliberate practice" su singoli temi relativi alla causality. Tutorial e riassunti saranno quindi al più delle "conseguenze" dell'esercizio che andrò a svolgere.

Questa nota si concentra principalmente sui Causal Graphs che ho avuto modo di conoscere in primis dal libro di Judea Pearl The Book of Why. Un'altra risorsa piuttosto utile trovata recentemente è ['Causal Inference for the Brave and True' by Matheus Facure Alves](https://matheusfacure.github.io/python-causality-handbook/landing-page.html)

## What is a Causal Graphs

A causal graph is a directed acyclic graph (aka DAG) which describes causal relations between a set of variables, which are represented by graphs' nodes. 
If $A \rightarrow B$ it means that $A$ causes $B$. 
Each variable is specifically a random variable. Hence. it is possible to infer the probability distribution on $B$ based the information given by $A$ thanks to Bayes' Rule. 

There are three main causal prototypes which can be identified and used to build all possible causal graphs:
* **Chains**: a sequences of $(A) \rightarrow (B) \rightarrow (C)$
* **Colliders**: such as $(A) \rightarrow (C) \leftarrow (B)$
* **Forks**: such as $(C) \leftarrow (A) \rightarrow (B)$

> [!note] Remark
> It is immediate that, if $A \rightarrow B$, then $A$ is correlated with $B$. Indeed, if it $A$ and $B$ are not correlated, they are independet r.v. and, consequently, 
> $$ 
>  \mathbb{P}(B | A) = \frac{\mathbb{P}(B \cap A)}{\mathbb{P}(A)} = \frac{\mathbb{P}(B)\mathbb{P}(A)}{\mathbb{P}(A)} = \mathbb{P}(B)
> $$
> This essentially means that information on A does not add knowledge related to B. Hence. a causal relationship cannot exists. 

Up to this point, we may ask if correlation implies causality. Except for the famous motto `Correlation is not causation`, we can easily build counterexamples by a causal graph which contains a fork to show that the opposite is not true and that correlation is a necessary but not sufficient condition. 
We may ask which additional hypothesis implies causality but this is above this section. 
## Causal Graphs and Data Science

In the previous section, we have seen how causal graphs are formally defined in probabilistic terms. The same terms are used in data science when we start facing the first problems related to classification or regression on (tabular) data. In general, this is a hint for a useful application. 

Assume that we need to predict a variable $Y$ using a set of features $X = (X_1, \ldots, X_n)$ and consequently build a causal graph containing $(Y, X)$. 
With dummy dataset, the given features $X$ are predictors of $Y$, however in real world scenario this is not granted and some "dirty" job on data is necessary. The same real world scenario have lead to iterative processes for data scientists to build un-biased ML models to be used in production. 
Some iteration of this process may be skipped "adding" additional information to our dataset in form of a causal graph. 
Some examples which came to my mind and that I have encountered in my working experience:

* **Business Knowledge (BK)**: every year the difficulties between data experts and business experts become stronger and stronger. BK is a key information to build effective data products and to accelerate their development. In this particular case, BK may confirm or exclude causal relations or provide information on causal direction
* **Data Generating Process (DGP)**: even if  *caused* by BK, it deserves a specific point. The details on DGP contains technical details, not related to BK, which help data scientists in removing redundant 

Based on BK and DGP, we can integrate or exclude causal relations in the graph. This step is rather important since it is a `knowledge-driven` feature selection process. 

>[!note] To Do
>* [ ] add list of potential bias (aka nodes to avoid)
>* [ ] add list of rules to understand independency
>* [ ] What happens with sequences (like text) or images?


>