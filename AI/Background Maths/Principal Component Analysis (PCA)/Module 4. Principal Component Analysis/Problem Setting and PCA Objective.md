#MachineLearning #PCA
#### By: Coursera - Mathematics for Machine Learning: PCA Week 4
---
### Objective
Assume we have a dataset $\mathbf{x} \in \mathbb{R}^D$:
$$
\mathcal{X} = \{ \mathbf{x}_{1},\dots \mathbf{x}_{N} \}, \text{ }\mathbf{x}_{n} \in \mathbb{R}^D
$$
Our ***objective*** is to find the **optimal lower-dimensional subspace** of our *data* that is as similar to $\mathbf{x}$ as possible, the subspace's dimension is $M < D$. Let us review three important concepts before delving deeper:
1. The *vectors* can be described as a **linear combination** of the **orthonormal basis vectors**.
$$
\mathbf{x}_{n} = \sum^D_{i=1} \beta_{in} b_{i}
$$
2. If we assume the ***inner product*** as the ***dot product***, we can interpret $\beta_{in}$ as the **coordinates** of the **[[Projection on Higher-Dimensional Subspaces|orthogonal projection]]** of $x_{n}$ onto the 1-dimensional *subspace* spanned by the $i$-th *basis vector*.
$$
\beta_{in} = \mathbf{x}_{n}^T b_{i}
$$
3. If we have a set of **orthonormal vectors** $B=\{ b_{1},\dots,b_{M} \}$ that form a *basis* for an $M$-dimensional subspace of $\mathbb{R}^D$. Then the projection of $\mathbf{x}$ onto the *subspace* can be written as:
$$
\tilde{\mathbf{x}} = B\underbrace{ B^T\mathbf{x} }_{ \text{Coordinates or code} }
$$
This means that $\tilde{\mathbf{x}}$ is the **orthogonal projection** of $\mathbf{x}$ onto the subspace spanned by the $M$ *basis vectors*. The ***coordinates*** or ***code*** is defined as $B^T \mathbf{x}$ and they are the coordinates of $\tilde{\mathbf{x}}$ with respect to the *basis vectors* collected in the matrix $B$. 

### PCA
The objective of ***PCA*** is to find the *lower-dimensional representation* $\tilde{\mathbf{x}}(\mathbf{x}_{n})$ that can be expressed using fewer *basis vectors*. We assume the data is **centered**, and also that $b_{1},\dots,b_{D}$ are *orthonormal bases* of $\mathbb{R}^D$.

1. $\text{Centered data: } E[X]=0$
2. $\text{ONB } b_{1},\dots,b_{D}$

Following what we saw in [[Orthogonal Complement and Decomposition]], we can write any $\mathbf{x}_{n}$ in the following way:
$$
\mathbf{x}_{n} = \sum^M_{i=1} \beta_{in}b_{i} + \sum^D_{i=M+1} \beta_{in}b_{i} \in \mathbb{R}^D
$$
In **PCA**, we are only interested in the *basis vectors* that span what we call the ***principal subspace*** ($b_{1},\dots, b_{M}$).
$$
\tilde{\mathbf{x}}_{n} = \sum^M_{i=1} \beta_{in}b_{i} \cancel{ + \sum^D_{i=M+1} \beta_{in}b_{i} \in \mathbb{R}^D }$$
### Setting
Assuming we have data $\mathbf{x}_{1},\dots \mathbf{x}_{N}$, we want to find the parameters $\beta_{in}$ and the **orthonormal basis** vectors $b_i$ such that the ***average square reconstruction error*** is ***minimized***.

We can write it as:

$$
J = \frac{1}{N} \sum^N_{n=1} \lvert\lvert \mathbf{x}_{n} - \tilde{\mathbf{x}}_{n}  \rvert\rvert^2
$$
In order to find the best possible fit, we have to find the **derivative** of $J$ with respect to the parameters $\beta_{in}, b_{i}$. Basically, we set the **partial derivatives** of $J$ with respect to these parameters to zero, and solve the ***optimal parameters***.

We can observe, however, that these parameters **only enter** the error function *through* $\tilde{\mathbf{x}}_{n}$, so we need to apply the ***chain rule*** to get our *partial derivatives*.
$$
\frac{\partial J}{\partial \{ \beta_{in},b_{i} \}} =  \frac{\partial J}{\partial \tilde{\mathbf{x}}_{n}} \frac{\partial\tilde{\mathbf{x}}_{n}}{\partial \{ \beta_{in}, b_{i} \}}
$$
Where:
$$
\frac{\partial J}{\partial \tilde{\mathbf{x}}_{n}} = -\frac{2}{N} (\mathbf{x}_{n} - \tilde{\mathbf{x}}_{n})^T
$$

