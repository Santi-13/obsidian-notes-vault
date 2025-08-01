#MachineLearning #PCA
#### By: Coursera - Mathematics for Machine Learning: PCA Week 3
---
We can further generalize the ***[[Projection onto 1D subspaces]]***. Let's look at this case where our vector $x$ lives in a three-dimensional space ($\mathbb{R}^3$)  and a **subspace** $u$ that spans $\mathbb{R}^2$ with **basis vectors** $b_1$ and $b_2$.

![[Orthogonal Projection into High-D]]

We observe a couple of things:
1. $\pi_{u}(x)$ can be represented as a linear combination of the *basis vectors* $b_1$ and $b_2$.
$$\pi_{u}(x)= \lambda_{1} b_{1} + \lambda_{2}b_{2}$$
2. The **difference vector** between $x$ and $\pi_{u}(x)$ is **orthogonal** to $u$, which means it is *orthogonal* for all *basis vectors* of $u$.
$$
\begin{matrix}
\langle x-\pi_{u}(x), b_{1} \rangle = 0 \\
\langle x-\pi_{u}(x), b_{2} \rangle = 0
\end{matrix}
$$

Or more generalized:
1. $\pi_{u}(x)=\sum^M_{i=1} \lambda_{i} b_{i}$
2. 