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
2. $\langle \pi_{u}(x)-x, b_{i} \rangle = 0, i= 1,\dots,M$
Where:
$$
\lambda = \underbrace{ \begin{bmatrix}
\lambda_{1} \\
\vdots \\
\lambda_{M}
\end{bmatrix} }_{ \text{M x 1} }, B = \underbrace{ \begin{bmatrix}
b_{1} & \dots & b_{M}
\end{bmatrix} }_{ \text{D x M} }
$$
With this definition we can write:
$$
\begin{matrix}
\pi_{u}(x)= B \lambda \\
\langle \pi_{u}(x)-x, b_{i} \rangle= \langle B\lambda-x, b_{i} \rangle= 0, i=1,\dots,M \\
\end{matrix}
$$
Assuming we choose he [[AI/Background Maths/Principal Component Analysis (PCA)/Module 2. Inner Products/Dot Product|Dot Product]] as our [[Inner Product]], we can use the second property and exploit the linearity of the **inner product** to:
$$
\begin{matrix}
\langle B\lambda,b_{i} \rangle - \langle x, b_{i} \rangle = 0, i=1,\dots,M \\
\lambda^TB^Tb_{i} - x^Tb_{i} = 0, i=1,\dots,M \\
\lambda^TB^TB - x^TB = 0^M \\
(\lambda^TB^TB=x^TB) (B^TB)^{-1} \\
\lambda^T=x^TB(B^TB)^{-1} \\
\text{As }(B^TB)^{-1} \text{ is symmetrical, its transpose is the same.} \\
\lambda=(B^TB)^{-1}B^Tx
\end{matrix}
$$
So our projection point would be:
$$
\pi_{u}(x) = B\lambda = B(B^TB)^{-1}B^Tx
$$
