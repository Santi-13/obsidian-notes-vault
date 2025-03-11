#Explanation #Chairing 
#### Direct kinematics
The open kinematic chain of the robot manipulator consists of its end-effector's pose:
$$
ς = DK(q)
$$
$$
ς=\begin{bmatrix}
x \\
y \\
z \\
\varphi \\
\theta \\
\psi
\end{bmatrix}
$$
And its velocity:
$$
\frac{d}{dt} ς(t) = \frac{d}{dt}DK(q(t))
$$
$$
=[\nabla_{q}DK(q(t))] \frac{d}{dt}q(t)
$$
$$
= J(q(t)) \frac{d}{dt}q(t)
$$
Along with its acceleration:
$$
\frac{d^2}{dt^2} ς(t) = \frac{d}{dt} \left(  J(q(t)) \frac{d}{dt} q(t) \right)
$$
$$
=\left[ \frac{d}{dt} J(q(t)) \right] \frac{d}{dt} q(t) + J(q(t)) \frac{d^2}{dt^2} q(t)
$$
#### Lagrangian Function
The Lagrangian $L$ is defined as the difference between the kinetic energy $K$ and the potential energy $V$ of the *system*:
$$
L(q, \dot{q}) = K(q, \dot{q}) - V(q)
$$
where $q$ represents the generalized coordinates, and $\dot{q}$ represents the generalized velocities.

#### Euler-Lagrange Equation
According to the ***Euler-Lagrange theory***, the dynamic motion of a mechanical system satisfies the following differential equation:
$$
\frac{d}{dt} \frac{\partial}{\partial \dot{q}_{j}} L(\dot{q},q) - 
\frac{\partial }{\partial {q}_{j}}L(\dot{q},q) = \phi_{j}^{\text{non-pot}} (\dot{q},q,t)
$$
Here, $\phi_{j}^{\text{non-pot}}$ represents **non-conservative** (non-potential) generalized forces acting on the system. For an ideal system without non-conservative forces, $\phi_{j}^{\text{non-pot}} = 0$.

These **non-conservative** generalized forces are those not derivable from a potential function (cannot be expressed as $-\nabla_{q}V$) such as $\tau$, **friction** and **constraint forces**.

We can get the ***Euler-Lagrange formulation*** of our system, starting from the standard **rigid-body dynamics**: ^3db8c3
$$
B(q)\ddot{q} + C(\dot{q},q)\dot{q} + G(q) = \tau
$$
$\text{Where:}$
$B(q): \text{Inertia matrix (symmetric, positive-definite)}$
$C(\dot{q},q): \text{Coriolis and centrifugal forces}$
$G(q): \text{Gravitational forces}$
$\tau: \text{ Actuator torques/forces}$

Solving for $\ddot{q}$:
$$
\ddot{q}= B^{-1}(q) (\tau-C(\dot{q},q) \dot{q} - G(q)
$$
We substitute in the equation for the end-effector's acceleration:
$$
\ddot{ς}(t) = \dot{J}(q) \dot{q} +J(q)
(\underbrace{ B^{-1}(q) [\tau-C(\dot{q},q) \dot{q} - G(q)] }_{ \ddot{q} }) 
$$
Which we can simplify:
$$
=f(q,\dot{q}) + g(q)\tau
$$
#### Applying Constraints
The system may be subject to constraints of the form:
$$
f_{k}(q) < 0, \text{ for } k=1,2,\dots,s,
$$
Where $f_{k}(q)$ defines a restriction on the generalized coordinates $q$. These may be *joint limits* or *collision avoidance* constraints. For example:
###### a) Joint angle limit:
$$
q_{1} < \frac{\pi}{2} \Longrightarrow f_{1}(q)=q_{1} - \frac{\pi}{2}
$$
The constraint is active when $f_{1}(q) \geq 0$.
###### b) Strict inequality transformation angle limit:
$$
q_{2}-\frac{\pi}{4} \leq 0
$$
We can introduce a *slack variable* $\mu>0$ in order to avoid edge cases where the equality might cause *singularities*.
$$
q_{2}-\frac{\pi}{4}+\mu < 0
$$
Now, we just need a way to enforce this constraints **only when violated**, this is where ***Lagrange Multipliers*** come in.


When the coordinates $q_j$ have constraints, we need to introduce Lagrange multipliers $\lambda_k(t)$ to incorporate these constraints into the **[[#Lagrangian Function]]**:
$$
L'(q, \dot{q}) = L(q, \dot{q})  + 
\sum^ς_{n=1} \lambda_{k}(t) f_{k} (q)
$$
where $f_k(q)$ represents the constraint equations and $\lambda_k(t)$ act as "smart weights" that dynamically adjust to enforce constraints based on other condition equations we set.

#### Euler-Lagrange Equation with Constraints 
Using the modified Lagrangian $L'$, the Euler-Lagrange equations becomes:
$$
\frac{d}{dt} \left( \frac{\partial L'}{\partial \dot{q}_{j}} \right) - 
\frac{\partial L'}{\partial {q}_{j}} = \phi_{j}^{\text{non-pot}}
$$
If the constraints are purely based on position, then the *partial derivative* of them with respect to $\dot{q}_{j}$ would become $0$, leaving us with the equation. So:
$$
\frac{d}{dt} \frac{\partial L'}{\partial \dot{q}_{j}} = \frac{d}{dt} \frac{\partial f_{k}}{\partial \dot{q}_{j}}
$$
While the constraint *does* depend on $q$:
$$
\frac{\partial L'}{\partial q_{j}} = \frac{\partial L}{\partial q_{j}} + \sum^ς_{n=1} \lambda_{k}(t) \frac{\partial f_{k}}{\partial q_{j}}
$$
Including the *non-conservative* forces, it all adds up to:
$$
\frac{d}{dt} \frac{\partial L}{\partial \dot{q}_{j}} - 
\frac{\partial L}{\partial {q}_{j}} = \phi_{j}^{\text{non-pot}} +
\sum^ς_{n=1} \lambda_{k}(t) \frac{\partial f_{k}}{\partial q_{j}}
$$
This is equivalent to its vector form:
$$
\frac{d}{dt} \begin{bmatrix} \frac{\partial}{\partial \dot{q}_{1}} L(\dot{q},q) \\ \vdots \\
\frac{\partial}{\partial \dot{q}_{n}} L(\dot{q},q) \end{bmatrix} - \begin{bmatrix}
\frac{\partial}{\partial q_{1}} L(\dot{q},q) \\ \vdots \\ \frac{\partial}{\partial q_{n}} L(\dot{q},q)  \end{bmatrix} =
\begin{bmatrix}
\phi_{1}^{\text{non-pot}} (\dot{q},q,t) \\ \vdots \\ \phi_{n}^{\text{non-pot}} (\dot{q},q,t) \end{bmatrix} + \begin{bmatrix}
\sum\nolimits_{k=1}^ς \lambda_{k}(t) \frac{\partial}{\partial q_{1}} f_{k}(q) \\ \vdots  \\
\sum\nolimits_{k=1}^ς \lambda_{k}(t) \frac{\partial}{\partial q_{n}} f_{k}(q)
\end{bmatrix}
$$
$$
\frac{d}{dt} \nabla_{\dot{q}} L(\dot{q},q) - \nabla_{q} L(\dot{q},q) = \phi^{\text{non-pot}}(\dot{q},q,t) +
\langle \lambda(t), f(q) \rangle 
$$
#### Defining Lagrange Equation
From our initial definition of the ***[[#Lagrangian Function]]***:
$$
L(q, \dot{q}) = K(q, \dot{q}) - V(q)
$$
We note that:
$$
K(\dot{q},q) = \frac{1}{2} \lvert\lvert \dot{q} \rvert\rvert_{B}^2 = \frac{1}{2} \dot{q}^TB\dot{q} 
$$
$$
V(q) = H(q)
$$
$\text{Where:}$
$K(\dot{q},q): \text{Proposed Lyapunov Function for the system's energy}$
$H(q): \text{Gravitational Potential Energy}$

We can then substitute on our ***[[#Euler-Lagrange Equation]]***:
$$
\frac{d}{dt} \nabla_{\dot{q}} (\frac{1}{2} \dot{q}^TB\dot{q} - \cancel{ H(q) }) - \nabla_{q} (\frac{1}{2} \dot{q}^TB\dot{q} - H(q)) = 
\phi^{\text{non-pot}}(\dot{q},q,t) +
\langle \lambda(t), f(q) \rangle 
$$
From ***[[Matrix Calculus Derivative Rules]]***, we get that the derivative or *gradient* of $\frac{1}{2} \dot{q}^TB\dot{q}$ is $B\dot{q}$, hence:
$$
\frac{d}{dt} \langle B(q),\dot{q} \rangle  -\frac{1}{2} \dot{q}^T [\nabla_{q}B(q)]\dot{q} + \nabla_{q}H(q) = \phi^{\text{non-pot}}(\dot{q},q,t) +\langle \lambda(t), f(q) \rangle 
$$
$$
\left( \frac{d}{dt} B(q) \right) \dot{q} + B(q) \ddot{q} - \frac{1}{2} \dot{q}^T [\nabla_{q}B(q)]\dot{q} + \nabla_{q}H(q) = \phi^{\text{non-pot}}(\dot{q},q,t) +\langle \lambda(t), f(q) \rangle 
$$
If we group up terms, we see some resemblance with our original ***[[#^3db8c3|rigid-body dynamics]]***:
$$
B(q)\ddot{q}+\underset{ C(\dot{q},q) }{ \left[ \frac{d}{dt} B(q)-\frac{1}{2} \dot{q}^T[\nabla_{q}B(q)] \right] }\dot{q} + \underset{ G(q) }{ \nabla_{q}H(q) } = 
\phi^{\text{non-pot}}(\dot{q},q,t) +\langle \lambda(t), f(q) \rangle 
$$
We can further divide the ***non-potential*** forces into **dissipative** (friction, damping) and **non-conservative** (friction, actuators, external disturbances) **forc**:
$$
B(q)\ddot{q} + C(\dot{q},q)\dot{q} + G(q) = \Omega\tau+ \phi_{diss}(\dot{q},q,t) + \langle \lambda(t), f(q) \rangle
$$
********
