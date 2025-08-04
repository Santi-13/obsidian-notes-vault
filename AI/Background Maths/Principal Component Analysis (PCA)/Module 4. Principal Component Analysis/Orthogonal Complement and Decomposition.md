#MachineLearning #PCA
#### By: Coursera - Mathematics for Machine Learning: PCA Week 4
---
### Complement
The ***Orthogonal Complement Theorem*** states that for a ***[[Vectors, Spaces & Subspaces|subspace]]*** $W$ in a ***vector space*** $\mathcal{V}$, there *exists* a *complement* $W^{\perp}$ which contains all *vectors* in $\mathcal{V}$ that are ***orthogonal*** to every vector in $W$. Informally, it is called the ***perp***, short for ***perpendicular complement***. It is also a **subspace** of $\mathcal{V}$.

If we look at an $n$-dimensional *vector space* $\mathcal{V}$ and a $k$-dimensional *subspace* $W \subset V$, then the **orthogonal complement** $W^{\perp}$ is an $(n-k)$-dimensional subspace of $\mathcal{V}$.

### Decomposition
It basically states that every vector $\mathbf{y}$ in $\mathbb{R}^n$ can be represented as the sum of a *vector* in a *subspace* $W$ of $\mathbb{R}^n$ and a *vector* in the *orthogonal complement* $W^\perp$ to $W$.

It can be written in the form:
$$
\mathbf{y} = \hat{\mathbf{y}}+\mathbf{z}
$$
Where $\hat{\mathbf{y}}$ is the ***[[Projection on Higher-Dimensional Subspaces|orthogonal projection]]*** of $\mathbf{y}$ onto the *subspace* $W$ and $\mathbf{z}$ is a vector orthogonal to $\hat{\mathbf{y}}$.
$$
\mathbf{z} = \mathbf{y} - \hat{\mathbf{y}}
$$
