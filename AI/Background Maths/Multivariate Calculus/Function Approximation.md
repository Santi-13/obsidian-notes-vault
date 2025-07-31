#MachineLearning #MultivariateCalculus
#### By: Coursera - Mathematics for Machine Learning Week 4
---
When working with complex functions, computing the whole function for each value is simply not worth it, specially when working between certain values of the graph. For this reason, we use ***function approximation*** to create a simpler polynomial equivalent of a function segment.

```desmos-graph
left=-5; right=3;
top=4; bottom=-8;
---
y=1*x^4+3.0*x^3+0.5*x^2
```

The ***Taylor (or Power) Series*** is a way of approximating functions. It is also called power series because it is simply composed of coefficients in front of increasing powers of $x$, so a generalized expression may be:
$$
g(x) = a + bx + cx^2 +dx^3 + \dots
$$
Where the equation may go on infinitely, depending on the function we're considering. For normal applications however, it is usually fine to use the first terms of the series. Starting from a single term, we call these expressions the zeroth, first, second, and third approximations, which are also in turn called *truncated series*.
$$g_{0}(x) = a$$
$$g_{1}(x) = a + bx$$
$$g_{2}(x)= a + bx + cx^2$$
$$g_{3}(x) = a + bx + cx^2 + dx^3$$
To approximate a function, we must focus on a singular point in the curve, and start building our approximations around it. The zeroth, first, second, and third order approximations for the above graph around point $(0,0)$ would look something like:

```desmos-graph
left=-5; right=3;
top=4; bottom=-8;
---
y=1*x^4+3.0*x^3+0.5*x^2+0.5*x
y=0|dashed|red
y=0.5*x|dashed
(0,0)|label:(0,0)|black
y=0.5*x+1*x^2|dashed
y=0.5*x+1*x^2+6x^3|dashed
```

This is basically what the ***Taylor Series*** method tells us, that if we know everything about a function at some point (value, its derivative, second derivative, etc.) we can use this information to reconstruct the function **everywhere** else. 

However, this is only true for a certain type of functions which we call *well-behaved* functions, which means a function that is continuous and that you can differentiate as many times as you want.

Now let's break down how we obtain the appropriate coefficients for the **Power Series** approximation, let's start with the zeroth approximation, which just uses the value of the function at our point of interest.
$$g_{0}= f(0)$$
Then, for the first order approximation, the value at the function will be the vertical axis intercept $c$ and the gradient will be the gradient at that point $m$.
$$g_{1}=f(0) + f'(0)x$$
Now, for the second order approximation, we must do a quadratic equation, which will hopefully reveal why we assumed the equation for the previous approximations:
$$y=f(x)=ax^2+bx+c$$
$$f'(x)=2ax+b$$
$$f''(x)=2a$$
From this, we can evaluate at our point $(0)$, starting from the biggest derivative, in order to get the coefficients for our approximation:
$$a = \frac{f''(0)}{2}$$
$$b=f'(0)$$
$$c = f(0)$$
So the second order approximation would be:
$$
g_{2}=f(0)+ f'(0)x + \frac{1}{2} f''(0)x^2
$$
We notice a pattern, as the third approximation would have to be derived three times, basically multiplying $1*2*3$, so:
$$
g_{2}=f(0)+ f'(0)x + \frac{1}{2} f''(0)x^2 + \frac{1}{6} f^{(3)}(0)x^3
$$
This operation has a name, and it is called the ***factorial***, we can now use this to describe a general expression for this approximation.
$$
g_{n}=\frac{f(0)}{0!}+ \frac{f'(0)x}{1!} + \frac{f''(0)x^2}{2!}+\dots+\frac{f^{(n)}(0)x^n}{n!}
$$$$
g(x) = \sum^\infty_{n=0} \frac{1}{n!}f^{(n)}(0)x^n
$$
Even though this approximation counts as a ***Taylor Series***, because we are specifically looking at the point $x=0$, we often refer to it as the ***Maclaurin Series***.

One interesting fact is that we can express $e^x$ as a power series:
$$
e^x=1+x+\frac{x^2}{2}+\frac{x^3}{6}+\dots
$$
We notice how its derivative its the same as itself, because of the infinitely extending polynomial.
$$
\frac{d}{dx}e^x=1+x+\frac{x^2}{2}+\frac{x^3}{6}+\dots = e^x
$$
Now the actual ***Taylor Series*** follows the same logic as the ***Maclaurin Series***, but the Taylor Series just says that there is nothing special about the point zero. So if you know anything about **any** point in the function, you can know *everything* about it.

Let's analyze it by getting the approximations for the function $y=e^x$ at $x=p$.

```desmos-graph
left=-5; right=3;
top=6; bottom=-2;
---
y=e^x
x=1|dashed|red
(1,e)|label:p|black
```
The zeroth order approximation is simply:
$$ g_{1} = f(p) $$
While the first order will have a gradient and will look like:
$$ y = mx+c $$We know the gradient is $f'(p)$, and that we are evaluating at $x=p$, so we must solve for $c$:
$$f(p)=f'(p)p+c$$
$$ c = f(p) - f'(p)p $$
Substituting back into the original equation:
$$
g_{2} = y= f'(p)x + f(p) - f'(p)p
$$
$$
g_{2}= f'(p) (x-p) + f(p)
$$
We notice that the subtraction is there to indicate how far away are we from the point $p$. We notice how the pattern is similar to the ***Maclaurin Series***, so we can finally write our short sum notation for the ***Taylor Series***.
$$
g(x) = \sum^\infty_{n=0} \frac{1}{n!}f^{(n)}(p)(x-p)^n
$$

### Flashcards
---
What is the difference between the ***Taylor*** & ***Maclaurin Series***?:: The ***Maclaurin Series*** says that if we know everything there is to know about a function at its origin, then we can know everything about the whole function. While the ***Taylor Series*** says that there is nothing special about the origin, and that if we know everything about any point in the function, we can approximate the functions as a whole.
<!--SR:!2025-08-27,28,290-->

