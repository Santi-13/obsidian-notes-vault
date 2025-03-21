#Chairing #Explanation
Let's now develop a similar ***Lyapunov function*** to the one we did in [[Lyapunov no Perturbations]], but adding a **perturbator** variable $v$ to $\dot{\mathrm{x}}$:
$$
\dot{\mathrm{x}} = A\mathrm{x} + v
$$
Now, the **perturbations** can be *internal* or *external*. An internal perturbation is often ***state-dependent***, which means that they are bounded and multiplicate the *state* of the *system*; While external perturbations are often *additive* and ***non-state dependent***.

We can bound our equation to these **perturbations** in two different forms in order to see the max of how these affect the system.
#### Multiplicative form
In this form, $v$ is **state-dependent**, so it can be bounded as:
$$
\lvert \lvert v \rvert  \rvert \leq v^+ \lvert\lvert \mathrm{x} \rvert\rvert, \text{ }v^+ > 0  
$$
Then:
$$
\frac{d}{dt} V(\mathrm{x}) = \langle P\mathrm{x}, A\mathrm{x}+v \rangle 
$$
$$
=\mathrm{x}^TP(A\mathrm{x} + v)
$$
$$
= \underbrace{ \mathrm{x}^TPA\mathrm{x} }_{ Nominal } + \underbrace{ \mathrm{x}^TPv }_{Perturbations}
$$
`We now must analyze the effect of the **perturbative term** to be able to properly analyze the maximum effect the perturbations can have in our system. 

We use the [[Cauchy-Schwarz Inequality]] to bound it. As $\mathrm{x}^TPv = \langle (P\mathrm{x})^Tv \rangle$:
$$
\lvert (P\mathrm{x})^T v \rvert \leq \lvert\lvert P\mathrm{x} \rvert\rvert \text{ }\lvert\lvert v \rvert\rvert  
$$
For a *symmetric matrix*, its ***induced Euclidian norm*** is defined as its largest *eigenvalue*.
$$
\lvert\lvert P \rvert\rvert = \lambda_{\text{max}} (P)
$$
We also note that the *product* of two norms is *equal* or *greater* than the norm of the product.
$$
\lvert\lvert P\mathrm{x} \rvert\rvert \leq \lvert\lvert P \rvert\rvert \text{ } \lvert\lvert \mathrm{x} \rvert\rvert
$$
Now we can substitute $\lvert\lvert v \rvert\rvert$ in our ***Cauchy-Schwarz Inequality***  with our initial bound for it.
$$
\lvert (P\mathrm{x})^T v \rvert \leq \lvert\lvert P \rvert\rvert \text{ }\lvert\lvert \mathrm{x} \rvert\rvert \text{ }\lvert\lvert v \rvert\rvert \leq 
\lvert\lvert P \rvert\rvert \text{ }\lvert\lvert \mathrm{x} \rvert\rvert v^+ \lvert\lvert \mathrm{x} \rvert\rvert
$$
Considering:
$$
\lvert\lvert P \rvert\rvert \text{ }\lvert\lvert \mathrm{x} \rvert\rvert v^+ \lvert\lvert \mathrm{x} \rvert\rvert = \lvert\lvert P \rvert\rvert v^+ \lvert\lvert \mathrm{x} \rvert\rvert^2
$$
$$
= \lvert\lvert P \rvert\rvert v^+ \mathrm{x}^T\mathrm{x} = \mathrm{x}^T \lvert\lvert P \rvert\rvert v^+I\mathrm{x} 
$$
Given all this, along with the analysis of the **nominal** term done [[Lyapunov no Perturbations|here]], we can bound the whole **Lyapunov function** as:
$$
\frac{d}{dt} V(\mathrm{x}) \leq -\frac{1}{2} \mathrm{x}^TQ\mathrm{x} + \mathrm{x}^T \lvert\lvert P \rvert\rvert v^+I\mathrm{x} < 0
$$
$$
\frac{d}{dt} V(\mathrm{x}) \leq \mathrm{x}^T \left( -\frac{Q}{2} + \lvert\lvert P \rvert\rvert v^+I \right) \mathrm{x} < 0
$$
#### Additive Form
In this form, $v$ is **not state-dependent**, so it can be bounded as:
$$
\lvert\lvert v \rvert\rvert \leq v^+ , \text{ }v^+ > 0  
$$
Following a similar analysis as before, we get:
$$
\frac{d}{dt} V(\mathrm{x}) = \underbrace{ \mathrm{x}^TPA\mathrm{x} }_{ Nominal } + \underbrace{ \mathrm{x}^TPv }_{Perturbations}
$$
We can **bound** the perturbation using the ***[[Peter-Paul Inequality]]*** for $\underbrace{ \mathrm{x}^TP }_{ x } \underbrace{ v }_{ y }$:
$$
\mathrm{x}^TPv \leq \frac{\theta}{2} \lvert\lvert \mathrm{x}^TP \rvert\rvert^2 + \frac{1}{2\theta} \lvert\lvert v \rvert\rvert^2,\text{ } \forall\theta > 0
$$
We can then use this to bound our ***Lyapunov function***:
$$
\frac{d}{dt} V(\mathrm{x}) \leq -\frac{1}{2} \mathrm{x}^TQ\mathrm{x} + 
\frac{\theta}{2} \mathrm{x}^TP^2\mathrm{x} + \frac{1}{2\theta} \lvert\lvert v \rvert\rvert^2
$$
Substituting our bound for $v$:
$$
\leq -\frac{1}{2} \mathrm{x}^TQ\mathrm{x} + 
\frac{\theta}{2} \mathrm{x}^TP^2\mathrm{x} + \frac{(v^+)^2}{2\theta} 
$$
$$
\leq \frac{1}{2} \mathrm{x}^T( \underbrace{ -Q + \theta P^2 }_{ Q_{1} } )\mathrm{x} + \frac{(v^+)^2}{2\theta} 
$$
Where $\theta P^2$ is the part of $Q_{1}$ that compensates for $v$. In order to achieve this overcoming the perturbations we must say that if:
$$
\frac{1}{2}( \underbrace{ -Q + \theta P^2 }_{ Q_{1} } ) \leq 0
$$
Then:
$$
\frac{d}{dt} V(\mathrm{x}) \leq \frac{1}{2}\mathrm{x}^TQ_{1}\mathrm{x} +\underbrace{  \frac{(v^+)^2}{2\theta} }_{ \beta }
$$
Here, to make sure that our nominal term overcomes the perturbative one, we can use the ***[[Rayleigh Quotient]]*** to bound $V(\mathrm{x})$:
$$
R(P,\mathrm{x}) = \frac{\mathrm{x}^TP\mathrm{x}}{\mathrm{x}^T\mathrm{x}}
$$
$$
\lambda_{\text{min}}(P) \leq \frac{\mathrm{x}^TP\mathrm{x}}{\mathrm{x}^T\mathrm{x}} \leq \lambda_{\text{max}}(P)
$$
$$
\lambda_{\text{min}}(P)\lvert\lvert \mathrm{x} \rvert\rvert^2  \leq \mathrm{x}^TP\mathrm{x} \leq \lambda_{\text{max}}(P)\lvert\lvert \mathrm{x} \rvert\rvert^2
$$
$$
\lambda_{\text{min}}(P)\lvert\lvert \mathrm{x} \rvert\rvert^2  \leq 2V(\mathrm{x}) \leq \lambda_{\text{max}}(P)\lvert\lvert \mathrm{x} \rvert\rvert^2
$$

Similarly, we can bound $Q_{1}$:
$$
\lambda_{\text{min}}(Q_{1})\lvert\lvert \mathrm{x} \rvert\rvert^2  \leq \mathrm{x}^TQ_{1}\mathrm{x} \leq \lambda_{\text{max}}(Q_{1})\lvert\lvert \mathrm{x} \rvert\rvert^2
$$
Disregarding the inequality, we can substitute $\mathrm{x}^TQ_{1}\mathrm{x}$ into the $\frac{d}{dt}V(\mathrm{x})$ equation:
$$
\frac{d}{dt}V(\mathrm{x}) \leq -\frac{1}{2} \lambda_{\text{min}}(Q_{1})\lvert\lvert \mathrm{x} \rvert\rvert^2 + \beta
$$
Now we can relate $\lvert\lvert \mathrm{x} \rvert\rvert^2$ to $V(\mathrm{x})$ from our [[Lyapunov With Perturbations#^1f77a9|bound]] of it:
$$
\lambda_{\text{min}}(P)\lvert\lvert \mathrm{x} \rvert\rvert^2\leq \mathrm{x}^TP\mathrm{x}
$$
$$
\lvert\lvert \mathrm{x} \rvert\rvert^2 \leq \frac{2V(\mathrm{x})}{\lambda_{\text{min}}(P)}
$$
Substituting we get:
$$
\frac{d}{dt} V(\mathrm{x}) \leq -\underbrace{ \frac{\lambda_{\text{min}}(Q_{1})}{\lambda_{\text{min}}(P)} }_{ \alpha } V(\mathrm{x}) + \beta
$$
Thus we get the final equation that provides ***ultimate boundedness*** to our *system*, ensuring trajectories stay near $x^{eq}$, even if they do not converge to it.
$$
\frac{d}{dt} V(\mathrm{x}) \leq -\alpha V(\mathrm{x}) + \beta
$$
Which has the following solution
$$
V(t) \leq V(0) e^{-\alpha t} + \frac{\beta}{a} ( 1 - e^{-\alpha t})
$$
