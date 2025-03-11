#MachineLearning #MultivariateCalculus
#### By: Coursera - Mathematics for Machine Learning Week 5
---
Similar to what we learned about the ***[[Newton-Raphson Method & Gradient Descent]]***, we can try something called ***Constrained Optimization***, which basically means finding the minima or maximum of a function *constrained* by another equation. For example, for the function $f(x)$ constrained by $g(x)$:
$$
f(x)=\exp\left( -\frac{2x^2+y^2-xy}{2} \right)
$$
$$
g(x) = x^2+3(y+1)^2-1=0
$$
![[Pasted image 20250122112011.png]]

![[Pasted image 20250122112039.png]]

This function has two minima and maxima. To find them, we use what we call ***Lagrange Multipliers***, which make use of the fact that the minima and maxima on the curve (or path) are found where the constraint is parallel to the contours of the function. Since they are parallel, the gradient of both will be parallel too, just not of the same magnitude exactly. So we can write the gradient of the constraint function $g(x)$ as a magnitude of $\nabla f(x)$:

This function has two minima and maxima. To find them, we use what we call ***Lagrange Multipliers***, which make use of the fact that the minima and maxima on the curve (or path) are found where the constraint is parallel to the contours of the function. Since they are parallel, the gradient of both will be parallel too, just not of the same magnitude exactly. So we can write the gradient of the constraint function $g(x)$ as a magnitude of $\nabla f(x)$: 
$$
\nabla f(x)=\lambda \nabla g(x)
$$
$$
\begin{bmatrix}
\frac{\partial f}{\partial x} \\
\frac{\partial f}{\partial y}
\end{bmatrix} = \lambda \begin{bmatrix}
\frac{\partial g}{\partial x} \\
\frac{\partial g}{\partial y}
\end{bmatrix}
$$
This equation, along with $g(x) = 0$ is enough to specify the system fully. We can put it all in a single vector equation $\nabla \mathcal{L}(x,y,\lambda)$:
$$
\nabla \mathcal{L}(x,y,\lambda) = \begin{bmatrix}
\frac{\partial f}{\partial x} - \lambda \frac{\partial g}{\partial x} \\
\frac{\partial f}{\partial y} - \lambda \frac{\partial g}{\partial y} \\
-g(x)
\end{bmatrix} = 0
$$
Now we have to find the zeros of this 3D vector equation, which may seem more complicated, but we have access to tools to make this easier, such as the previously discussed ***[[Newton-Raphson Method & Gradient Descent|Newton-Raphson Method]]*** or by using existing libraries. To solve this particular system in Python, we may do something similar to this:

```
from scipy import optimize

# First we define the functions,
def f (x, y) :
    return np.exp(-(2*x*x + y*y - x*y) / 2)  

def g (x, y) :
    return x*x + 3*(y+1)**2 - 1

# Next their derivatives,
def dfdx (x, y) :
    return 1/2 * (-4*x + y) * f(x, y)

def dfdy (x, y) :
    return 1/2 * (x - 2*y) * f(x, y)

def dgdx (x, y) :
    return 2*x

def dgdy (x, y) :
    return 6*(y+1)  

def DL (xyλ) :
    [x, y, λ] = xyλ
    return np.array([
            dfdx(x, y) - λ * dgdx(x, y),
            dfdy(x, y) - λ * dgdy(x, y),
            - g(x, y)
        ])

(x0, y0, λ0) = (1, -1, 0)
x, y, λ = optimize.root(DL, [x0, y0, λ0]).x

print("x = %g" % x)
print("y = %g" % y)
print("λ = %g" % λ)
print("f(x, y) = %g" % f(x, y))
print("g(x, y) = %g" % g(x, y))
```