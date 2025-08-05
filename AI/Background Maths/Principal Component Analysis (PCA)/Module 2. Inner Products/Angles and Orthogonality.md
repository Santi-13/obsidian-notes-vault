#MachineLearning #PCA
#### By: Coursera - Mathematics for Machine Learning: PCA Week 2
---
***Orthogonality*** is central to projections and dimensionality reduction. Similar to lengths and distances, the ***angle*** between two vectors is defined through the ***[[Inner Product]]***. 

If we have to vectors $x$ and $y$, we can use the following relationship: ^5845b1
$$
\cos \omega = \frac{\langle x,y \rangle }{|| x || \text{ } || y ||}
$$
Where $\omega$ is the **angle** between *vectors*. 

Two *vectors* are said to be ***orthogonal*** if and only if their **inner product** is zero. This also means that ***orthogonality*** is based on the definition we use for the **inner product**. 

For vectors $x = \begin{bmatrix}1 \\  1\end{bmatrix}$, $y = \begin{bmatrix}-1  \\ 1\end{bmatrix}$:

```graph
bounds: [-3.5, 1.5, 3.5, -1.5]
elements: [ 
	{type: arrow, def: [[0,0], [1,1]] },
	{type: arrow, def: [[0,0], [-1,1]] },

]
```

They are ***orthogonal*** because their inner product is zero. 

We can also find ***basis vectors*** that are ***orthogonal*** to each other, we do this by **normalizing** the vectors. Which we end up calling an ***orthonormal basis***.
