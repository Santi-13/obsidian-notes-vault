#MachineLearning #PCA
#### By: Coursera - Mathematics for Machine Learning: PCA Week 4
---
We informally characterize ***vectors*** as objects that can be *added* together and *multiplied* by a *scalar*value. Formally, however, **vectors** are what we denominate as ***Groups***. 

Consider a **set** $\mathcal{G}$ and an operation (such as $+$, $-$, $*$, $/$, etc.) $\otimes$ that takes two inputs in the set and produces an output in that same set ($\otimes:\mathcal{G} \to \mathcal{G}$). Then we can define the set equipped with the operation as $\mathcal{G}:=(\mathcal{G},\otimes)$). Then $\mathcal{G}$ is called a **group** if the following properties hold:

1. $\text{Closure of } \mathcal{G} \text{ under } \otimes: \forall x,y \in \mathcal{G}: x \otimes y \in \mathcal{G}$
2. $\text{Associativity}: \forall x,y,z\in \mathcal{G} : (x\otimes y)\otimes z=x\otimes(y\otimes z)$
3. $\text{Neutral element}: \exists e\in \mathcal{G}\forall x \in G: x \otimes e=x \text{ and } e\otimes x=x$
4. $\text{Inverse element}: \forall x \in \mathcal{G} \exists y \in \mathcal{G} : x \otimes y = e \text{ and } y \otimes x = e. \text{ Often written as } x^{-1}.$

If, additionally to this, this property is followed:

5. 
