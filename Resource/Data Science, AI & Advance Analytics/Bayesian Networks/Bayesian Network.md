---
source:
---
## Definition

A **Bayesian Network (BN)** is a Directed Acyclic Graph (DAG) $G = (X, E)$ where $X$ is the set of vertices, $E$ is the set of arches.
The vertices $X = {X1, X2, · · · , Xn}$ represent *(discrete)* random variables.
Each variable $X_i$ is annotated with a conditional probability distribution (CPD) $P(X_i |par(X_i))$, where $par(X_i)$ denotes the set of parents of $X_i$ in $G$. 

The BN represents a joint distribution P(X1, X2, · · · , Xn) given as, 
	$$P(X_1, X_2, ... , X_n) = \Pi_i P(X_i |par(X_i)).$$
Be aware that the graph arches are a prior explicit knowledge of dependance between variables. 

Since for a BN is a probability distribution, we have that $\Pi_i P(X_i|par(X_i)\leq 1$ and $\sum_{x_1, ..., x_n} \Pi_i P(x_i |par(x_i)) = 1$.
## Local Markov property

### Markov blanket

### d-separation

# Sources
* [Bayesian Networks by J.Larrosa](https://www.cs.upc.edu/~larrosa/MEI-CSI-files/BN/csi-apuntes-bn.pdf)