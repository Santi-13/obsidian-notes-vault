#MachineLearning #MultivariateCalculus
#### By: Coursera - Mathematics for Machine Learning 
---
When you have a single function of many variables:
$$
f(x_{1},x_{2},x_{3},\dots)
$$
The Jacobian of that function can be described as a vector of the partial derivatives of the function.
$$
J=\left[ \frac{\partial f}{\partial x_{1}}, \frac{\partial f}{\partial x_{2}},\frac{\partial f}{\partial x_{3}},\dots\right]
$$
By convention, we write this as a row vector, instead of a column vector. Let's analyze an example to gather some deeper intuition on the subject. For a function:
$$
f(x,y,z)=x^2y+3z
$$
It's Jacobian vector looks like:
$$
J=[2xy,x^2,3]
$$
This vector describes which variables affect the rate of change of each variable in the function, for example, the vector tells us that:

- How $f(x,y,z)$ changes with respect to $x$, depending on the magnitude of $2xy$, that is, as the product becomes larger, changes in $x$ become more significant.
- How the significance in changes in $y$ are proportional to $x^2$.
- How $z$ always increase or decrease the function's value by $3$ units.

In other words, the Jacobian represents the rate of change of a multivariate function, and evaluating it at certain points creates a vector indicating the direction and rate of the function's steepest slope, becoming smaller as the coordinates approach maximum, minimum or saddle points. 

![[Pasted image 20241016125602.png]]

We can extend this concept to matrices, with a Jacobian matrix, which allows us to describe the rate of change of a vector valued function, which is simply a function that has more than one input, as well as more than one output. One example can be when trying to convert from polar coordinates to cartesian coordinates:

![[Pasted image 20241020144627.png]]

We can describe the cartesian coordinates in this equation as:
$$ x(r,\theta)=r\cos (\theta) $$
$$ y(r,\theta)=r\sin (\theta) $$
Or as a vector valued function:
$$
F(x,y) = \begin{bmatrix}
r\cos(\theta) \\
r\sin(\theta)
\end{bmatrix}
$$
We can then calculate the Jacobian matrix of it, each value telling us what values affect the rate of change of the function with respect to some input value:
$$ J = \begin{pmatrix} \frac{\partial x}{\partial r} & \frac{\partial x}{\partial \theta} \\ \frac{\partial y}{\partial r} & \frac{\partial y}{\partial \theta} \end{pmatrix} = \begin{pmatrix} \cos(\theta) & -r \sin(\theta) \\ \sin(\theta) & r \cos(\theta) \end{pmatrix} $$
For example, here we see that the rate of change of $x$ with respect to $r$ is proportional to the value of $cos(\theta)$. We can also obtain the determinant of the Jacobian matrix, which would tell us how space scales, which helps us linearize a system.
$$\det(J) = |J| = r(\cos^2(\theta)+\sin^2(\theta))$$
$$ |J| = r $$
![[Pasted image 20241020150028.png]]

### Flashcards
---
What is a [[Jacobian]]?
?
A Jacobian describes the rate of change of each variable in a multivariate function. We can have a Jacobian vector when having a multivariate function, or a Jacobian matrix when we have a vector-valued function. For example:
$$ x(r,\theta)=r\cos (\theta) $$
$$ y(r,\theta)=r\sin (\theta) $$
$$
F(x,y) = \begin{bmatrix}
r\cos(\theta) \\
r\sin(\theta)
\end{bmatrix}
$$
<!--SR:!2025-01-25,4,270-->
What is the [[Jacobian]] useful for?:: The Jacobian of a function can help us find the minimum or maximum of a multivariate function without needing to evaluate the whole function, just its Jacobian on specific points. As the evaluated Jacobian serves as a "direction" towards a critical point.
<!--SR:!2026-05-01,275,330-->