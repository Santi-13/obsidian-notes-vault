#MachineLearning #PCA
#### By: Coursera - Mathematics for Machine Learning: PCA Week 1
---
The intuitive definition of the ***[[Variance of 1D Datasets|Variance]]*** we explored doesn't really work in high dimensions, and *squaring* vectors is not really defined.

In the example of a 2d dataset, we may be able to compute the ***variance*** of each dimension, but we may also be interested in the relationship between this variables. This is where the concept of a ***covariance*** between these components comes into play. The ***covariance*** between a dimension $x$ and $y$ is defined as follows:
$$
\text{cov}[x,y] = \text{E}[(x-\mu_{x})(y-\mu_{y})]
$$$\text{Where:}$
$$\mu_{x}=\text{E}[x]$$
$$\mu_{y}=\text{E}[y]$$
Finally, we can identify four quantities of interest for this dataset, the two ***covariances***, as well as the two ***variances***. We summarize this values in what we call the ***covariance matrix***.
$$
M = \begin{bmatrix}
\text{var}[x] & \text{cov}[x,y] \\
\text{cov}[y,x] & \text{var}[y]
\end{bmatrix}
$$
If the ***covariance*** between $x$ and $y$ is *positive*, then on average the $y$ value increases if we increase $x$, and vice-versa. The ***covariance matrix*** is always a *symmetric*, *positive definite* matrix, which means that the determinant of itself, as well as that of its **minors** are greater than zero.

We can generalize for a $\text{D-dimensional}$ dataset. For: $D=\{ x_{1},\dots,x_{n} \}, x \in \mathbb{R}^D$.
$$
\text{var}[D]=\frac{1}{N}\sum^n_{n=1}(x_{i}-\mu)(x_{i}-\mu)^T
$$
---
#### Flashcards
What is the ***[[Variance of Higher-Dimensional Datasets|covariance matrix]]***?:: Is a *symmetric*, *positive definite* matrix that explains the relation between components of a dataset.
<!--SR:!2025-08-01,2,190-->

