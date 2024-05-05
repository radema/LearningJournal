---
source:
---
## Definition

A **Bayesian Network (BN)** is a Directed Acyclic Graph (DAG) $G = (X, E)$ where $X$ is the set of vertices, $E$ is the set of arches. 
The vertices $X = {X1, X2, · · · , Xn}$ represent *(discrete)* random variables.
Each variable $X_i$ is annotated with a conditional probability distribution (CPD) $P(X_i |par(X_i))$, where $par(X_i)$ denotes the set of parents of $X_i$ in $G$. 

The BN represents a joint distribution $P(X_1, X_2, · · · , X_n)$ given as, 
	$$P(X_1, X_2, ... , X_n) = \Pi_i P(X_i |par(X_i)).$$
Be aware that the graph arches are a prior explicit knowledge of dependance between variables. 

Since for a BN is a probability distribution, we have that
* $P(X_1, X_2, ... , X_n) = \Pi_i P(X_i|par(X_i)\leq 1$ 
* $\sum_{x_1, ..., x_n} P(x_1, x_2, ... , x_n) = \sum_{x_1, ..., x_n} \Pi_i P(x_i |par(x_i)) = 1$.

One key property of BNs is that they are **efficient** representations of **exponentially large probability** distributions.

> Storing a BN requires space $O(n · k^p )$, where n is the number of variables, k is the size of the largest domain among the variables, and p is the maximum number of parents among all the variables (the reason is that we only need to store the graph and the CPDs). The BN represents a probability distribution of O(n k ) entries (i.e, one for each possible assignment of the random variables). 

> [!note] Remark
> A Bayesian Network is a [[Generative Model]]. 


## Local Markov property

### Markov blanket
_X_ is a Bayesian network with respect to _G_ if it satisfies the **local Markov property**: each variable is [conditionally independent](https://en.wikipedia.org/wiki/Conditional_independence "Conditional independence") of its non-descendants given its parent variables:

$$𝑋_𝑣 ⊥⊥ (𝑋_{𝑉∖de⁡(𝑣)}∣𝑋_{pa⁡(𝑣)}),$$  $\forall 𝑣\in𝑉,$ where $de(v)$ is the set of descendants of $v$. 

** The [Markov blanket](https://en.wikipedia.org/wiki/Markov_blanket "Markov blanket") of a node is the set of nodes consisting of its parents, its children, and any other parents of its children. 
* The Markov blanket renders the node independent of the rest of the network; 
* the joint distribution of the variables in the Markov blanket of a node is sufficient knowledge for calculating the distribution of the node. 
### d-separation

If X is a Bayesian network then every node is conditionally independent of all other nodes in the network, given its [Markov blanket](https://en.wikipedia.org/wiki/Markov_blanket "Markov blanket").


## Useful applications

The knowledge related to a BN distribution allow to compute probabilities and queries of interests. In this section, we detail some of the most relevant:
* **Prior marginals:** given $X_i$ a random variable, we can calculate $P(X_i)$ as $$P(X_i) = \sum_{j \not= i} P(x_1, x_2,...,x_{i-1},x_i,x_{i+1},...,x_n)$$
* **Posterior marginals**: given $X_i$ and posterior knowledge $z$ related to other variables, it is possible to update our marginals by Bayes rule $$P(X_i | z) = \frac{P(X_i, z)}{P(z)},$$ where each component in the ratio can be calculated by probability definition
* **Maximum A Posteriori Hypothesis (MAP):** given Y ⊂ X a set of variables of interest and Z ⊂ X a set of variables whose value has been observed, we want to know the most probable configuration for Y , given an instantiation z  of Z $$y^∗ = \arg \max_y P(Y |z).$$
All these queries can be numerically computed using the [[Variable Elimination Algorithm]] 

# Python Libraries

* [sorobn by Max Halford](https://github.com/MaxHalford/sorobn?tab=readme-ov-file) : `The main goal of this project is to be used for educational purposes. As such, more emphasis is put on tidyness and conciseness than on performance.` 
* [pomegranate](https://pomegranate.readthedocs.io/en/latest/): `Python package that implements fast and flexible probabilistic models ranging from individual probability distributions to compositional models such as Bayesian networks and hidden Markov models. [...] One can create a Bayes classifier that uses different types of distributions on each features, perhaps modeling time-associated features using an exponential distribution and counts using a Poisson distribution. Lastly, since these compositional models themselves can be viewed as probability distributions, one can build a mixture of Bayesian networks or a hidden Markov model Bayes’ classifier that makes predictions over sequences.`
	* [[General Mixture Models]]
	* [[Bayes Classifier]]
	* [[Hidden Markov Models]]
	* [[Markov Chains]]
	* [[Bayesian Network]]
	* [[Factor Graphs]]
* [pgmpy](https://pgmpy.org/) `pure python implementation for Bayesian Networks with a focus on modularity and extensibility. Implementations of various alogrithms for Structure Learning, Parameter Estimation, Approximate (Sampling Based) and Exact inference, and Causal Inference are available.`
* [BNLearn](https://erdogant.github.io/bnlearn/pages/html/index.html) : `_bnlearn_ is for learning the graphical structure of Bayesian networks in Python! What benefits does bnlearn offer over other bayesian analysis implementations?
	- `Build on top of the pgmpy library
    - `Contains the most-wanted bayesian pipelines
	- `Simple and intuitive
	- `Focus on structure learning, parameter learning and inference.
	`
* [pyMC](https://www.pymc.io/projects/docs/en/stable/learn.html) `probabilistic programming library for Python that allows users to build Bayesian models with a simple Python API and fit them using Markov chain Monte Carlo (MCMC) methods`
* [CausalNex](https://causalnex.readthedocs.io/en/latest/01_introduction/01_introduction.html) `Python library that uses Bayesian Networks to combine machine learning and domain expertise for causal reasoning. You can use CausalNex to uncover structural relationships in your data, learn complex distributions, and observe the effect of potential interventions.`
# Sources
* [Bayesian Networks by J.Larrosa](https://www.cs.upc.edu/~larrosa/MEI-CSI-files/BN/csi-apuntes-bn.pdf)
* https://en.wikipedia.org/wiki/Bayesian_network
* https://www.bayesserver.com/docs/