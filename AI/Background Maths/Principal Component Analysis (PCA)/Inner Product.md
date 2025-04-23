#MachineLearning #PCA
#### By: Coursera - Mathematics for Machine Learning: PCA Week 2
---
An ***inner product*** is a generalization of the ***[[AI/Background Maths/Principal Component Analysis (PCA)/Dot Product|Dot Product]]*** that allows us to measure the *geometric properties* of **vectors** (angles, distances and lengths). This includes complex vectors.

For any vectors $u,v,w$ in a vector space $V$, the ***inner product*** is a function that, similarly to the ***dot product***, outputs a scalar in $\mathbb{R}$ or $\mathbb{C}$. 
$$
\langle ⋅, ⋅ \rangle : V \times V \to \mathbb{R} \text{ or } \mathbb{C} 
$$
It has to be **symmetric**:
$$
\langle u,v \rangle= \langle v,u \rangle 
$$
**Positive definite**:
$$
\langle u,u \rangle \geq 0 \text{ and } \langle u,u \rangle =0 \iff u=0
$$
And **bilinear**, that is, linear in both of its arguments, for a constant $\lambda$:
$$
\langle \lambda u,v \rangle=c \langle u,v \rangle  
$$
$$
\langle u+v,w \rangle =\langle u,w \rangle + \langle v,w \rangle 
$$
$$
\langle \lambda u+v,w \rangle = \lambda \langle u,w \rangle +\langle v,w \rangle 
$$
$$
\beta(\mathrm{x}, \mathrm{y}) = \mathrm{x}^T \begin{bmatrix}
2 & 1 \\
-1 & 1
\end{bmatrix} \mathrm{y}
$$