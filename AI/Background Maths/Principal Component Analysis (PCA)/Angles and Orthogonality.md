#MachineLearning #PCA
#### By: Coursera - Mathematics for Machine Learning: PCA Week 2
---
***Orthogonality*** is central to projections and dimensionality reduction. Similar to lengths and distances, the ***angle*** between two vectors is defined through the ***[[Inner Product]]***. 

If we have to vectors $x$ and $y$, we can use the following relationship:
$$
\cos \omega = \frac{\langle x,y \rangle }{|| x || \text{ } || y ||}
$$
Where $\omega$ is the **angle** between *vectors*. 

Two *vectors* are said to be ***orthogonal*** if and only if their **inner product** is zero. This also means that ***orthogonality*** is based on the definition we use for the **inner product**.

```desmos-graph
left=-4; right=14;
top=2; bottom=0;
---
f(x)=1
(-1,1)|black|label:D
(2,1)|black
(3,1)|black
(1,1)|blue
(4,1)|blue|label:D'
(5,1)|blue
(-2,1)|orange
(4,1)|orange|label:D''
(6,1)|orange

(4/3,1)|black|cross|label:E[D]
(10/3,1)|blue|cross|label:E[D']
(8/3,1)|orange|cross|label:E[D'']
```
