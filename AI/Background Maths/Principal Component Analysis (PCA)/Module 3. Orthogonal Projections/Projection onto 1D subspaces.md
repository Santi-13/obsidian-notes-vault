#MachineLearning #PCA
#### By: Coursera - Mathematics for Machine Learning: PCA Week 3
---
For ***PCA***, it is crucial we identify the directions that describe our data the most, to later **project** our data into these new directions. To understand ***orthogonal projection*** into a ***1D subspace***, let's see this example:

![[Orthogonal Projection into 1D]]

Here, $x$ is a point that can be described as the linear combination of the **basis vectors** of $\mathbb{R}^2$, $u$ is a 1D subspace with a basis vector $b$ —that is, all vectors in $u$ can be described as $\lambda b$. 

To find the *orthogonal projection*, we want to find the $u$ *vector* which is closest to $x$. 

![[Orthogonal Projection into 1D closest]]

That means that the **difference vector** of $x$ and its *projection* is *orthogonal* to $u$. We can denote this *projection* as $\pi_{u}(x)$, and it has two very important **properties**:
1. As $\pi_{u}(x)$ lives in the subspace $u$, there exists a $\lambda$ value for which the projection can be described in terms of the subspace's basis vector.
$$\pi_{u}(x) \in u \implies \exists \lambda \in \mathbb{R}: \pi_{u}(x) = \lambda b$$
2. The difference vector between the point and its *projection* is *orthogonal* to the *basis vector* that spans $u$. That is:
$$\langle b, \pi_{u}(x)-x \rangle = 0 $$
We can exploit these properties to help us find the projection $\pi_{u}(x)$.
$$
\begin{matrix}
\langle b, \pi_{u}(x)-x \rangle = 0 \\
\langle b, \pi_{u}(x) \rangle-\langle b, x \rangle = 0 \\
\langle b, \lambda b \rangle-\langle b, x \rangle = 0 \\
\lambda \lvert\lvert b \rvert\rvert^2 -\langle b, x \rangle = 0 \\
\lambda = \frac{\langle b, x \rangle}{ \lvert\lvert b \rvert\rvert^2 } \\
\implies \pi_{u}(x) = \lambda b = \frac{\langle b, x \rangle}{ \lvert\lvert b \rvert\rvert^2 } b
\end{matrix}
$$
If we then choose he [[AI/Background Maths/Principal Component Analysis (PCA)/Module 2. Inner Products/Dot Product|Dot Product]] as our [[Inner Product]], we can further rewrite this:
$$
\frac{\langle b, x \rangle}{ \lvert\lvert b \rvert\rvert^2 } b = \frac{ b^Txb}{ \lvert\lvert b \rvert\rvert^2 } 
$$
Given that $b^Tx$ is a scalar, we can move it around such that:
$$
\underbrace{ \frac{ bb^T }{ \lvert\lvert b \rvert\rvert^2 }  }_{ \text{Projection Matrix} } x = \pi_{u}(x)
$$
Now we can use this ***projection matrix*** to project any point in the two dimensions to the subspace $u$.