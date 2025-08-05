#MachineLearning #PCA
#### By: Coursera - Mathematics for Machine Learning: PCA Week 4
---
Assume we have a dataset $\mathbf{x} \in \mathbb{R}^D$:
$$
\mathbf{x} = \{ \mathbf{x}_{1},\dots \mathbf{x}_{N} \}, \mathbf{x}_{i} \in \mathbb{R}^D
$$
Our ***objective*** is to find the **lowest** dimensional representation of our *data* that is as similar to $\mathbf{x}$ as possible. Let us review three important concepts before delving deeper:
1. The *vectors* can be described as a **linear combination** of the **orthonormal basis vectors**.
$$
x_{n} = \sum^D_{i=1} \beta_{in} b_{i}
$$
2. If we assume the ***inner product*** as the ***dot product***, we can interpret $\beta_{in}$ as the **[[Projection on Higher-Dimensional Subspaces|orthogonal projection]]** of $x_{}$also write that:
$$
\beta_{in} = x_{n}^T b_{i}
$$