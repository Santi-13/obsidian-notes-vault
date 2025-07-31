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
g(x)=\sin(x)\cos(x)
```

We see that this function is ***odd***, which means that:
$$
f(-x) = -f(x)
$$
If we choose the integral limits to be $-\pi$ and $\pi$, then it would evaluate to $0$, meaning that sine and cosine are **orthogonal**.

Another example for defining an ***inner product*** between **unusual types** are **random variables** or **random vectors**. If we have two random variables, which are uncorrelated, we know the following relationship:
$$
var[x+y] = var[x] + var[y]
$$
If we remember our generalized **variance** definition:
$$
\text{var}[D]=\frac{1}{n}\sum^n_{n=1}(x_{i}-\mu)(x_{i}-\mu)^T
$$
We can see the relationship looks much like the ***Pythagorean Theorem*** for right triangles:
$$
c^2= a^2 + b^2
$$
With this, we can try to find a ***geometric interpretation*** of the variance relation of uncorrelated **random variables**, which can be considered **elements** in a **vector**. And we can define ***inner products*** to obtain geometric properties of them. If we define it as, for example:
$$
\langle x,y \rangle = cov[x,y]
$$
We see that the ***covariance*** is *positive*, *definite*, and *linear*. **Linearity** would mean that:
$$
cov[\lambda x+y,z] = \lambda cov[x,z] + cov[y,z]
$$
Then, to [[Length or Norm of a vector#^269bff|obtain the length]] of this **random variable**, we get that it is its **standard deviation**, as:
$$
\lvert\lvert x \rvert\rvert = \sqrt{ \langle x,x \rangle } = \sqrt{ cov[x,x] } = \sqrt{ var[x] } = \sigma(x) 
$$
Now if we [[Angles and Orthogonality#^5845b1|look at the angles]] between two **random variables**, we get:
$$
\cos \theta =  \frac{ \left\langle  x,y \right\rangle}{ \lvert\lvert x \rvert\rvert \text{ } \lvert\lvert y \rvert\rvert  }
$$
$$
=  \frac{ cov[x,y] }{ \sqrt{ var[x] var[y] } }
$$
We see that the covariance between them would be zero **if and only if** $x$ and $y$ are ***uncorrelated***. Though it is important to note that just because two variables are *uncorrelated*, it doesn't mean they are ***independent*** from each other.

The goal of ***Principal Component Analysis*** is to find a new, orthogonal basis for the feature space. In the language of random variables, PCA transforms the original, correlated features (which can be seen as non-orthogonal vectors) into a new set of **uncorrelated** features called **principal components**. These new features are, by definition, **orthogonal** under the covariance inner product. PCA finds the directions (eigenvectors of the covariance matrix) in the data with the highest variance ("length").