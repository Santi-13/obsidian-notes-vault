#MachineLearning #MultivariateCalculus
#### By: Coursera - Mathematics for Machine Learning Week 3
---
When we have a multi-variable function, such as $f(x,y,z)$, but the variables themselves are a function of some other variable $t$. If we want to get the derivative of $f$ with respect to $t$, which is simply the sum of the chains relating $f$ to $t$ through each variable. This is called the ***Total Derivative***. For example:
$$
f(x,y,z)=\sin(x)e^{yz^2}
$$
$$
x=t-1 ;\text{ }y =t^2;\text{ } z=\frac{1}{t}
$$
$$
\frac{df}{dt}=\frac{\partial f}{\partial x} \frac{\partial x}{\partial t}
+ \frac{\partial f}{\partial y} \frac{\partial y}{\partial t}
+ \frac{\partial f}{\partial z} \frac{\partial z}{\partial t}
$$
This allows us to calculate the result in a piece-wise manner instead of substituting everything, which is something computers are very good at. We can generalize this concept as follows:
$$
f(x_{1}, x_{2},x_{3},\dots,x_{n})=f(\pmb{x})
$$
$$
\frac{\partial f}{\partial \pmb{x}} = \begin{bmatrix}
\frac{\partial f}{\partial x_{1}} \\
\frac{\partial f}{\partial x_{2}} \\
\frac{\partial f}{\partial x_{3}} \\
\vdots \\
\frac{\partial f}{\partial x_{n}}
\end{bmatrix} \text{ }\text{ }
\frac{\partial \pmb{x}}{\partial t} = \begin{bmatrix}
\frac{\partial x_{1}}{\partial t} \\
\frac{\partial x_{2}}{\partial t} \\
\frac{\partial x_{3}}{\partial t} \\
\vdots \\
\frac{\partial x_{n}}{\partial t}
\end{bmatrix}
$$
$$
\frac{df}{dt} =\frac{\partial f}{\partial \pmb{x}} \cdot \frac{d \pmb{x}}{d t}
$$
One detail we may notice is that $\frac{\partial f}{\partial \pmb{x}}$ is just the [[Jacobian]] of $f$, but in a column instead of a row vector. 
$$
\frac{\partial f}{\partial \pmb{x}} = J_{f}^T
$$
Then, we can replace the dot product with a much more convenient representation
$$
\frac{df}{dt} =J_{f}\frac{\partial \pmb{x}}{\partial t}
$$
We can also prove that the chain rule works for more than two links. Let's analyze an example:
$$f(x)=5x$$
$$x(u)=1-u$$
$$u(t)=t^2$$
Then, by simple substitution we can find that:
$$ f(t) = 5(1-t^2) = 5 - 5t^2 $$
$$
\frac{df}{dt}=-10t
$$
Or we can also apply the chain rule such as:
$$
\frac{df}{dt} =\frac{d f}{d x}  
\frac{d x }{d u}
\frac{d u }{d t}
$$
$$
\frac{df}{dt} = (5)(-1)(2t)=-10t
$$
In the multivariate case we get the same result, though it is still interesting to analyze. For:
$$f(\pmb{x}(\pmb{u}(t)))$$
$$f(\pmb{x})=f(x_{1},x_{2})$$
$$\pmb x(\pmb u)= \begin{bmatrix}
x_{1}(u_{1},u_{2}) \\
x_{2}(u_{1},u_{2})
\end{bmatrix}$$
$$\pmb u(t)= \begin{bmatrix}
u_{1}(t) \\
u_{2}(t)
\end{bmatrix}$$
At the end, the math works out as the derivative ends up like:
$$
\frac{df}{dt}=J_{\pmb x}J_{\pmb u} \frac{d \pmb u}{dt}
$$
