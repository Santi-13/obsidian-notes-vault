#MachineLearning #PCA
#### By: Coursera - Mathematics for Machine Learning: PCA Week 2
---
The ***Inner*** or ***Dot Product*** allows us to talk about **geometric** properties in a **vector space**. 

A familiar example may be the ***Dot Product*** between two vectors $x,y \in \mathbb{R}^n$, which is defined as:
$$
x \cdot y = x^Ty = \sum_{i=1}^n x_{i}y_{i} 
$$
The **length** or **magnitude** of $x$ is defined as the *square root* of the **dot product** of $x$ with itself.
$$
\lvert\lvert x \rvert\rvert = \sqrt{ x^Tx } = \sqrt{ x\cdot x } = \sqrt{ \sum^n_{i=1} x_{i}^2 }
$$
For two vectors $x=\begin{bmatrix}1 \\ 2\end{bmatrix}$ and $y=\begin{bmatrix}2 \\ 1\end{bmatrix}$, we are interested in the **distance** and **angle** between them. 
![[Pasted image 20250423114148.png]]

The **distance** is simply defined as the square root of the ***dot product*** of the difference of the vectors:
$$
d(x,y) = \lvert\lvert x-y \rvert\rvert = \sqrt{ 2 } 
$$
The **angle** between vectors $\alpha$ is defined as:
$$
\cos \alpha = \frac{x^Ty}{\lvert\lvert x \rvert\rvert \text{ } \lvert\lvert y \rvert\rvert} = 0.64 \text{ rad} 
$$
From this, we can see another definition for the ***dot product***, the **projection** of one vector length onto another:
$$
x^Ty=\cos \alpha \lvert\lvert x \rvert\rvert \text{ } \lvert\lvert y \rvert\rvert
$$