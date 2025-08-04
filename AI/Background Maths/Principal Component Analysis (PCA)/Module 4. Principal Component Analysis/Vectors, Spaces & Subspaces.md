#MachineLearning #PCA
#### By: Coursera - Mathematics for Machine Learning: PCA Week 4
---
We informally characterize ***vectors*** as objects that can be *added* together and *multiplied* by a *scalar* value. Formally, however, **vectors** are what we denominate are ***sets*** and, when associated with certain **operators**, we get the algebraic structure of ***groups***.

### Groups
Consider a **set** $\mathcal{G}$ and an operation (such as $+$, $-$, $*$, $/$, etc.) $\otimes$ that takes two inputs in the set and produces an output in that same set ($\otimes:\mathcal{G} \to \mathcal{G}$). Then we can define the set equipped with the operation as $\mathcal{G}:=(\mathcal{G},\otimes)$). Then $\mathcal{G}$ is called a **group** if the following properties hold:

1. $\text{Closure of } \mathcal{G} \text{ under } \otimes: \forall x,y \in \mathcal{G}: x \otimes y \in \mathcal{G}$
2. $\text{Associativity}: \forall x,y,z\in \mathcal{G} : (x\otimes y)\otimes z=x\otimes(y\otimes z)$
3. $\text{Neutral element}: \exists e\in \mathcal{G}\forall x \in G: x \otimes e=x \text{ and } e\otimes x=x$
4. $\text{Inverse element}: \forall x \in \mathcal{G} \exists y \in \mathcal{G} : x \otimes y = e \text{ and } y \otimes x = e. \text{ Often written as } x^{-1}$

If, additionally to this, this property is followed:

5. $\text{Commutative}: \forall x,y \in \mathcal{G}: x \otimes y = y \otimes x$

Then $\mathcal{G}$ is an ***Abelian group***.

### Vector Spaces
As we initially informally described, a *real-valued* ***vector space*** is a set $\mathcal{V}$ with an additional **inner operation** (mapped within itself):

- $\text{Can be added together}$
$$
+: \mathcal{V} \otimes \mathcal{V} \to \mathcal{V}
$$
And an **outer operation** (interacts with other groups):

- $\text{Can be multiplied by a scalar}$
$$
\cdot : \mathbb{R} \otimes \mathcal{V} \to \mathcal{V}
$$
Where the following hold:
1. $(\mathcal{V},+)$ is an *Abelian group*.
2. $\text{Distributibity:}$
	1. $\lambda \cdot(\mathbf{x}+\mathbf{y}) = \lambda\cdot \mathbf{x} + \lambda\cdot \mathbf{y}$       $\forall \lambda \in \mathbb{R},\mathbf{x},\mathbf{y} \in \mathcal{V}$
	2. $(\lambda+\psi) \cdot \mathbf{x} = \lambda\cdot \mathbf{x}+\psi\cdot \mathbf{x}$       $\forall \lambda,\psi \in \mathbb{R},\mathbf{x} \in \mathcal{V}$
3. $\text{Associativity (outer operation):} \lambda\cdot(\psi\cdot \mathbf{x}=(\lambda \psi))\cdot \mathbf{x}$        $\forall \lambda \in \mathbb{R},\mathbf{x},\mathbf{y} \in \mathcal{V}$
4. $\text{Neutral element with respect to the outer operation:} 1\cdot \mathbf{x}=\mathbf{x}, \forall \mathbf{x} \in \mathcal{V}$
Then the elements $\mathbf{x}$ in the **vector space** $\mathcal{V}$ are called ***vectors***. 

### Vector Subspaces
In short, ***vector subspaces*** are **sets** contained in the original **vector space** that when we perform *vector space operations* on elements within this **subspace**, we never leave it. In this sense, they are *"closed"*.

If we let $(\mathcal{V},+,\cdot)$ be an $\mathbb{R}$-vector space and $\mathcal{U}$ is a **subset** of $\mathcal{V}$ ($\mathcal{U} \subseteq \mathcal{V}$), $\mathcal{U} \neq 0$. Then $U= (\mathcal{U},+,\cdot)$ is a **vector (or linear) subspace** of $\mathcal{V}$ if $U$ is a **vector space** with the *vector space operations* $+$ and $\cdot$ restricted to $\mathcal{U}\times\mathcal{U}$ and $\mathbb{R} \times \mathcal{U}$. 

