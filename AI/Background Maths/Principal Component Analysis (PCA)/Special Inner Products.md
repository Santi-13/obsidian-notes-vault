#MachineLearning #PCA
#### By: Coursera - Mathematics for Machine Learning: PCA Week 2
---
The ***[[Inner Product]]*** we previously discussed could be described as **discrete functions** with a **finite** number of function **values**. But the concept of an ***inner product*** can be further generalized to include ***continuous functions***. And then the *sum* over individual components of *vectors* turns into an *integral*. 

The ***inner product*** between two functions is defined as:
$$
\langle u, v \rangle = \int^b_{a} u(x) v(x) dx
$$
As with the regular ***[[Inner Product]]***, we can define the ***norms*** and ***orthogonality*** by looking at this product. If the **integral** evaluates to **zero**, the functions $u$ and $v$ are **orthogonal**. For example, for:
$$
\begin{matrix} 
u(x) = \sin(x) \\
v(x) = \cos(x)  \\
f(x) = u(x)v(x)
\end{matrix}
$$
We end up with this function:

```desmos-graph
left=-4; right=4;
top=0.6; bottom=-0.6;
---
f(x)=\sin(x)\cos(x)
```

