#MachineLearning #PCA
#### By: Coursera - Mathematics for Machine Learning: PCA Week 2
---
The **length** or ***norm*** of a vector $x$ is defined as:
$$
|| x || = \sqrt{ \langle x, x \rangle} 
$$
Now it depends on how we define the ***[[Inner Product]]***, for instance if we define it as the standard ***[[Excalidraw/Dot Product|Dot Product]]***:
$$
\langle x,y \rangle = x^Ty
$$
Then for a vector $x = \begin{bmatrix}1 \\ 1\end{bmatrix}$:
$$
|| x || = \sqrt{ 2 }
$$
But if we define it in a more unconventional way, such as:
$$
\langle x,y \rangle = x^T \begin{bmatrix}
1 & -\frac{1}{2} \\
-\frac{1}{2} & 1
\end{bmatrix} y
$$
$$
|| x || = \sqrt{ 1 }
$$
The ***norm*** has also some properties:
$$
\begin{matrix}
|| \lambda x || = | \lambda |\text{ } || x|| \\
\underbrace{ || x + y|| \leq || x || \text{ } || y || }_{ \text{Triangle Inequality} }
\end{matrix} 
$$
Another inequality important to mention is the ***[[Cauchy-Schwarz Inequality]]***.
