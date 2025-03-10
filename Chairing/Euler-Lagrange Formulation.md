#Explanation #Chairing 
#### Direct kinematics
The open kinematic chain of the robot manipulator consists of its end-effector's pose:
$$
\zeta = DK(q)
$$
$$
\zeta=\begin{bmatrix}
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
\frac{d}{dt} \zeta(t) = \frac{d}{dt}DK(q(t))
$$
$$
=[\nabla_{q}DK(q(t))] \frac{d}{dt}q(t)
$$
$$
= J(q(t)) \frac{d}{dt}q(t)
$$
Along with its acceleration:
$$
\frac{d^2}{dt^2} \zeta(t) = \frac{d}{dt} \left(  J(q(t)) \frac{d}{dt} q(t) \right)
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

We can get the ***Euler-Lagrange formulation*** of our system, starting from the standard **rigid-body dynamics**:
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
\ddot{q}= B^{-1}(q) (\tau-C(\dot{q},q) \dot{q} - G(q))
$$
We substitute in the equation for the end-effector's acceleration:
$$
\ddot{\zeta}(t) = \dot{J}(q) \dot{q} +J(q)
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
\sum^\zeta_{n=1} \lambda_{k}(t) f_{k} (q)
$$
where $f_k(q)$ represents the constraint equations and $\lambda_k(t)$ act as "smart weights" that dynamically adjust to enforce constraints based on other condition equations we set.

#### Euler-Lagrange Equation with Constraints 
Using the modified Lagrangian $L'$, the Euler-Lagrange equations becomes:
$$
\frac{d}{dt} \left( \frac{\partial L'}{\partial \dot{q}_{j}} \right) - 
\frac{\partial L'}{\partial {q}_{j}} = \phi_{j}^{\text{non-pot}}
$$
If the constraints are purely based on position, then the *partial derivative* of them with respect to $\dot{q}_{j}$ would become $0$, leaving us with the equation.

The resulting equations describe the dynamics of the system while accounting for the constraints. For a system with dissipation and external forces, the equation can be expressed as:
$$
B(q) \ddot{q} + C(q,\dot{q}) \dot{q} + G(q) =
\tau + Q_{\text{diss}}(q, \dot{q}, t) + (\lambda(t), f(q))
$$
where $B(q)$ is the inertia matrix, $C(q, \dot{q})$ is the Coriolis and centrifugal forces matrix, $G(q)$ is the gravitational forces vector, $\tau$ is the control input, and $Q_{\text{diss}}(q, \dot{q}, t)$ represents dissipative forces.

$$
\frac{d^2}{dt^2} \zeta(t) = \left[\frac{d}{dt} J(q(t))\right] \frac{d}{dt} q(t) + J(q(t)) \left(M^{-1}(q) \left(\tau(t) - C(q(t), \frac{d}{dt} q(t)) \frac{d}{dt} q(t) - G(q(t))\right)\right)
$$
$$
=f\left( q ( t, \frac{d}{dt} q(t)) \right) +
g(q(t)) \tau(t)
$$
Where $M^{-1}(q)$ is the inverse of the **inertia matrix**, $\tau(t)$ is the control **torques** applied to the joints, and $C(q(t), \frac{d}{dt} q(t)) \frac{d}{dt} q(t)$ accounts for the effect of the Coriolis and centrifugal forces.

