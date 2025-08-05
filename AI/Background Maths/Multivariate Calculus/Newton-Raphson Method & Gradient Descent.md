#MachineLearning #MultivariateCalculus
#### By: Coursera - Mathematics for Machine Learning Week 5
---
The ***Newton-Raphson Method*** is an iterative approach to finding a desired solution to a equation just by evaluating the function and its derivative at certain points. Instead of having to plot the entire function. It is described as:
$$
x_{i+1} = x_{i}- \frac{f(x_{i})}{f'(x_{i})}
$$
For example, for the function $f(x)=x^3-2x+2$:
$$
f'(x_{i})=3x^2-2
$$

```desmos-graph
left=-4; right=4;
top=4; bottom=-4;
---
f(x)=x^3-2x+2
(1,e)|label:x|black
```

Suppose we want to find the point $y=0$, we start by analyzing an initial guess $x_i=-2$:

```desmos-graph
left=-4; right=4;
top=4; bottom=-4;
---
f(x)=x^3-2x+2
g(x)=3x^2-2 |red|dashed
(-2,f(-2))|label:xi|black
```

| $i$ | **$x_{i}$** | **$f(x_i)$** | **$\frac{\partial f(x_{i})}{\partial x}$** |
|:---:| ----------- | ------------ | ------------------------------------------ |
|  0  | -2          | -2           | 10                                         |
|  1  | -1.8        | -0.23        | 7.7                                        |
|  2  | -1.77       | -0.005       | 7.4                                        |
|  3  | -1.769      | -2.3E-6      |                                            |

We find, however, that this method is not infallible as a number of things can go wrong. For starters, if the desired solution is near an inflection point, the derivative will be very low, thus the movement from our initial guess will be very extreme; in the other hand, there can be initial guesses in a function that has us locked down in a closed-loop, never reaching the desired solution.

The ***Gradient Vector*** is another name for the ***[[Jacobian]] vector***, which always points towards the steepest ascent of the point it is evaluated at.

![[Pasted image 20250121123535.png]]

$$
\nabla f = J^T= \begin{bmatrix}
\frac{\partial f}{\partial x} \\
\frac{\partial f}{\partial y}
\end{bmatrix}
$$
Now if we were to move from that point in a certain unit vector direction $\hat{r}$, then we would have a *directional gradient*: 
$$
df=\nabla f \cdot \hat{r} = \begin{bmatrix}
\frac{\partial f}{\partial x} \\
\frac{\partial f}{\partial y}
\end{bmatrix} \cdot \begin{bmatrix}
c \\
d
\end{bmatrix}
$$
To find the optimal direction to move in, we need to optimize the best values for $\hat{r}$. For that, let us remember that the dot product of two vectors is the projection of the first unto the second. Which can be expressed in terms of an angle $\theta$:
![[Excalidraw/Dot Product]]
$$
df =|\nabla f| \cdot |\hat{r}| \cdot \cos(\theta)
$$
The maximum value of the $cos$ is $1$ (when $\hat{r}$ is aligned with $\nabla f$), and $\hat{r}$ is a unit vector so its magnitude is also $1$; From this, we observe that the maximum value of the directional gradient is equal to the magnitude of the ***Gradient Vector*** or ***[[Jacobian]]***.

We connect this with the ***Newton-Raphson Method*** as it is basically what we call the ***Gradient Descent Method***, in which we take little steps towards a minimum.
$$
S_{n+1} = S_{n} - \gamma \nabla f(S_{n})
$$

![[Pasted image 20250121125945.png]]

If we wanted to find the *minima* of a function, we could use a magnitude $\gamma$ (gamma), multiplied by our gradient (or ***[[Jacobian]]***), i.e.:
$$
\delta \text{x} = \gamma \pmb J
$$
Then we can try different values for $\gamma$; but this can make us overshoot or undershoot, so we have to come up with a better solution. A way to automatically determine the jump size is to use the ***[[Hessian]]***, then the step size can be given as:
$$
\delta \text{x} = -\pmb H^{-1}\pmb J
$$
This not only sets the step size, but can also change direction too. This method is as likely to find the maxima as it is the minima.
### Flashcards
---
What is the ***Newton-Raphson Method***?:: The ***Newton-Raphson Method*** is an iterative approach to finding the roots of an equation without having to calculate every possible value.
<!--SR:!2025-08-17,18,230-->

