#ml #AI 

## RankNet
[RankNet by Microsoft](https://www.microsoft.com/en-us/research/wp-content/uploads/2005/08/icml_ranking.pdf)

Ranking Task: build an utility function to rank items per each users
Ranking can be done using a scoring function $f:\mathbb{R}^d \to \mathbb{R}$ .

Given $o_i = f(x_i)$ and $o_{ij} = f(x_i) - f(x_j)$ , we define the cross entropy cost function:
$$ C_ij = C(o_{ij}) = - \overline{P}_{ij}\log{P_{ij}} - (1 - \overline{P}_{ij})\log{(1 - P_{ij})},$$
where $\overline{P}_{ij}$ are the desired target values for posterior probabilities and the probabilities $\overline{P}_{ij}$ are defined using the logistic function $$P_{ij} = \frac{e^{o_{ij}}}{1 + e^{o_{ij}}}.$$
Hence, $$C_{ij} = -\overline{P}_{ij}o_{ij} + \log(1 + e^{o_{ij}}).$$
The above definition leads naturally to a consistency definition of posterior probabilities. Consequentially, this puts a constraint on them as
$$\overline{P_{ik}} = \frac{\overline{P}_{ij}\overline{P}_{jk}}{1 + 2\overline{P}_{ij}\overline{P}_{jk} - \overline{P}_{ij} - \overline{P}_{jk}}$$
For this implies the complete uncertainty ($P = 0.5$) or complete certainty ($P \in \{0,1\}$) propagates to all probabilities.

Then in the paper, they assume a neural network to model $o_i$ and then apply a simple SGD strategy to determine the result.

Questions: the poster probabilities are unique?
The theorem states that given a subset of posterior probabilities entries, the others are determined. What about the first one? This seems similiar to the problem of clustering by MFG. Is it possible to adopt a fixed point theorem? It seems so but I'm not sure that uniqueness (up to permutation or dataset probably) is given. 

It is reasonable to assume that convergence has some kind of stability towards always the same output since the model is stated following a cost function and some desired target. Otherwise, the ranking system would not be suitable for usage. Remember that the cost function (aka matrix...) is model using logistic functions and cross entropies. This leads to a cost function which is defined by a log-noise and a linear term. The log term goes to zero for $f(x_i) >> f(x_j)$ . Moreover, the $o$ definition and the cross entropy definition in some way "contract" the dynamic itself constraing the evolution on a probability simplex (which is compact). 