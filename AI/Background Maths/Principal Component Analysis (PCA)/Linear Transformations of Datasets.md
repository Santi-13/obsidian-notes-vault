#MachineLearning #PCA
#### By: Coursera - Mathematics for Machine Learning: PCA Week 1
---
When working with datasets, we need to know how transforming the dataset (either by **stretching** or **shifting** the *dataset*) affects our quantities of interest (the ***[[Mean of a dataset|mean]]*** & the ***[[Variance of Higher-Dimensional Datasets|(co)variance]]***).

Consider three datasets, and their expected values:
$$
D=\{ -1,2,3 \}, E[D]=\frac{4}{3}
$$
$$
D'= D+2 = \{ 1,4,5 \}, E[D']= \frac{10}{3}
$$
$$
D''= 2D=\{ -2,4,6 \}, E[D'']=\frac{8}{3}
$$
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

We notice that in the case of the dataset **shifting** by 2, the ***mean*** just becomes two plus what it was; While in the **stretching** case, we multiply the previous ***mean*** by a *scaling factor*. So:
$$
E[D+a] =a +E[D]
$$
$$
E[aD]=aE[D]
$$
On the other hand, let's consider dataset's $D$ and $D'$ ***variance***.
$$
Var[D]=\frac{1}{n}\sum^n_{n=1}\left( x_{n}- \frac{4}{3} \right)^2 = - \frac{7}{3} + \frac{2}{3} + \frac{5}{3}  
$$