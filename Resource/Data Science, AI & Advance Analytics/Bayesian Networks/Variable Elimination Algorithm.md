* Given a DAG $G = (X, E)$, the **descendants** of $X_i$ are all the variables that can be reached from $X_i$ following the directed arches in E. 
* A **trail** is a path of length $k$ is a sequence of vertices $(X_{i1} , X_{i2} , · · · , X_{ik} )$ such that there is no repetition and there is an arch, no matter in which direction, between any pair of consecutive variables. A trail between from variable X to Y is indicated as $X \rightarrow Y$.

* Let A, B, C be three consecutive variables in a trail. We say that they form a **v-structure** is their arrows go as A → B ← C. 
* We say that a trail $(X_{i1} , X_{i2} , · · · , X_{ik} )$ is **active given Z** ⊂ X if for every v-structure in the trail either its middle or one of its descendants is in Z. 
* **Property**: Consider a BN with graph $G = (X, E)$. Let Y, W, Z be disjunct subsets of X. If there is no active trail between Y and W given Z, then Y ⊥W|Z

* Consider a set of random variables $X = {X_1, X_2, · · · , X_n}$ and let $Y$ be a subset of $X$. A **probabilistic factor** $τ (Y )$ is a function that associates a number to each possible assignment of the variables in $Y$ . $Y$ is called the scope of the factor. The size of $Y$ is the **arity** of the factor. 

* **Conditioning**: Consider a factor $τ$ with scope $Y$ and a variable $X_i ∈ Y$ . Conditioning τ with $x_i$ is a new factor with scope $$Y' = Y − {X_i},$$noted $τ [x_i ]$ and defined as, $$τ [x_i ](y' ) = τ (y' , xi).$$ The idea of conditioning is to fix one of the variables with a certain values.

* **Marginalization**: Consider a factor $τ$ with scope $Y$ and a variable $X_i ∈ Y$ . The marginalization of $τ$ with $X_i$ is a new factor with scope $Y' = Y − {X_i}$, noted $τ [X_i]$ and defined as, $$τ [ X_i ](y' ) = \sum_{x_i} τ (y 0 , x_i).$$ The idea of marginalization is to forget a variable. The individual contribution of the different values of a variable is replaced by its global contribution. 
* **Product**: Consider two factors $τ(Y )$ and $τ' (Y' )$. Their product is a new factor with scope $Z = Y \cup Y'$ , noted $τ · τ'$ and defined as, $(τ · τ' )(z) = τ (y) · τ' (y 0 )$ where $y$ and $y'$ are the part of $z$ that instantiate $Y$ and $Y'$ , respectively. The product is the inverse of a factorization.

We are going to use the concept of factor in the Variable Elimination algorithm, so its relevant to think about how factors can be stored in a computer. For the purpose of this notes, we will assume that factors are stored explicitly as tables. Thus, the size of a factor is its number of entries which is the product of domain sizes of all the variables in its scope. Note that an obvious consequence is that it is unfeasible to compute factors with large domains.


# Single Variable Elimination 

Consider a set of factors $\Theta = {τ_1, τ_2, · · · , τ_r}$ whose scopes $Y_1, Y_2, · · · , Y_r$ are subsets of $X = {X_1, X_2, · · · , X_n}$. 
We define here an algorithm that eliminates an arbitrary variable $X_i$ from the set of factors $\Theta$. 
The algorithm goes as follows: 
1. Compute $\Gamma = \{ τ_j ∈ \Theta| X_i ∈ Y_j \}$, which is the set of factors that have $X_i$ in their scope. 
2. Compute a new factor $τ$ as the product of all the factors in $\Gamma$ and subsequently marginalizing $X_i$ . Formally, $τ = (\Pi_{τ_j \in \Gamma} τ_j )[X_i ]$. Note that the scope of $τ$ is the union of all the scopes of the factors in $\Gamma$ except $X_i$ (i.e, $(\cup_j Y_j ) − {X_j})$. 
3. Replace in $\Theta$ all the factors in $\Gamma$ by the new factor $τ$. 
<!-- add a graphical example-->

The intuition of the algorithm is that the new factor τ can replace all the factors in $\Gamma$ because it contains the same information. 
**Function VarElim($X_i$ , Θ)** : return a set of factors equivalent to $\Theta$ but without $X_i$
**begin**
1. $Γ = \{τ_j ∈ Θ| X_i ∈ Y_j\}$,  
2. $τ = (\Pi_{τ_j ∈ Γ} τ_j )[X_i ]$; 
**return $(Θ − Γ) ∪ \{τ\}$;** 
**end** 


### Sources:
* https://www.cs.upc.edu/~larrosa/MEI-CSI-files/BN/csi-apuntes-bn.pdf