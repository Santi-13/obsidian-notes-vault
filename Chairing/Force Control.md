#Explanation #Chairing 

One reason to use ***Force Control*** in robotics system is that they *interact* with their environment, which means that the forces they apply to their surroundings are applied back to them, which may cause unintended side effects if not considered in their control laws.

To use ***Force Control*** means that I can make an interaction of my system with its environment behave according to the desired task.

We define as a **kinematic constraint** as an object that *constraints* the geometric paths that can be followed by the *end-effector*. This situation corresponding to contact with a stiff surface, is generally referred to as *constrained motion*.

In other cases, the contact task is characterized by a dynamic interaction that can be:
- Inertial (pushing a block)
- Dissipative (sliding on a surface with friction)
- Elastic (pushing against an elastically compliant wall)

### From Indirect Force Control to Hybrid Force/Motion Control

***Indirect Force Control*** refers to **impedance control (or admittance control)**, where the deviation of the end-effector motion from the desired motion due to the interaction with the environment is related to the contact force through a mechanical impedance/admittance with adjustable parameters.

To do this, we assume a reference frame $\Sigma_{e}$ at the end of the end-effector. A position vector $p_{e}$ and a rotation matrix $R$ from the origin. This allows us to find either a velocity, position, or force vector that originates from the end-effector, in terms of the origin.

It's velocity is denoted by a $6 \times 1$ vector $v_c = \begin{bmatrix}\dot{p}_{c}  \\ \omega_{c}\end{bmatrix}$, where $\dot{p}_{c}$  is the translational velocity, and $\omega_{c}$ is the rotational velocity. And can be computed from the $n$\*1 joint velocity vector $\dot{q}$ using the linear mapping:
$$
v_{c} = J(q) \dot{q}
$$
![[Diagram Force Transformations]]

The **force** $f_{e}$ and moment $m_e$ applied by the end-effector to the environment are the components of the wrench $h_e$.
$$
h_{e} = \begin{bmatrix}
f_{c}^T, m_{e}^T
\end{bmatrix}
$$
It is useful t o consider the operational space formulation of the dynamic model of a rigid robot manipulator in contact with the environment.
$$
\underbrace{ \Lambda(q)\dot{v}_{c} + \Gamma(q,\dot{q})v_{c} + \eta(q) }_{ \text{Newton's Second Law} } = \underbrace{ h_{c} - h_{e} }_{ \text{Force Differences} }
$$

Where:
$$
\Lambda(q)^{-1} = (J(q)H^{-1}(q)J^T(q))^{-1}
$$
There are different

#### Stiffness Control
In the classical operational space formulation, the end-effector *position* and *orientation* is described by a $6 \times 1$ vector $x_e= (p_{e}^T,\varphi_{e}^T)$. Where $\varphi_{e}$ is...
$$
\tau = M\ddot{q}+C\dot{q}
$$
#### Control de fuerza
La idea principal es parecida al resto de controladores en el sentido de que tenemos un sistema con retroalimentación, cuyo error se alimenta a un controlador para llegar a una trayectoria deseada.

Normalmente, el sistema lo representamos con las formulas de [[Euler-Lagrange Formulation|Euler-Lagrange]].
$$
B(q)\ddot{q} + C(\dot{q},q)\dot{q} + G(q) = \tau + \underbrace{ \eta(q,\dot{q},t) }_{ \text{incertidumbre} }
$$
Cuando el *sistema* se encuentra con un objeto, podríamos agregar esto a nuestro termino de *incertidumbre*, pero esto se considera una mala idea ya que controlamos a pesar de la incertidumbre.

En vez de esto, **agregamos** un término de **torque externo**, ocasionalmente llamado **external *wrench***.
$$
B(q)\ddot{q} + C(\dot{q},q)\dot{q} + G(q) = \tau + \underbrace{ \eta(q,\dot{q},t) }_{ \text{incertidumbre} } - \underbrace{ J^T(q)F_{EF}
 }_{ \text{Fuerza Externa} }$$
Cabe aclarar que **no** estamos controlando la fuerza de las juntas, sino que simplemente estamos aplicando una acción en contra de la fuerza encontrada. 

##### Indirect Force Control
When the end-effector makes contact with, for example, a wall, we want it to stop, or in other words:
$$
\ddot{q}=\dot{q}=0
$$
We dismiss the non-static noise, leaving us with:
$$
\cancel{ B(q)\ddot{q} } + \cancel{ C(\dot{q},q)\dot{q} } + G(q) = \tau + \underbrace{ \eta(q,\dot{q},t) }_{ \text{incertidumbre} } - \underbrace{ J^T(q)F_{EF}
 }_{ \text{Fuerza Externa} }
$$
$$
\underbrace{ G(q)- \eta }_{ \tilde{\eta} }= \tau- J^T F_{EF}
$$
Then, we can propose our *control action* $\tau$ so we can dismiss the remaining **system dynamics** $\tilde{\eta}$.
$$
\tau=\tilde{\eta}+J^T F_{EF}
$$
If instead of the end-effectors **experienced force**, we use a **desired force vector**.
$$
\tau= \tilde{\eta}+J^T F_{D}
$$
We can then substitute in our **systems equation**:
$$
 G(q) = \tilde{\eta}+J^T F_{D} +  \eta -  J^TF_{EF}
$$
$$
 \cancel{ G(q) =  G(q) } \cancel{ - \eta + \eta } +J^T F_{D}  -  J^TF_{EF}
$$
$$
J^T(F_{D}-F_{EF}) = 0
$$
This basically tells us that, for any ***non-singularity*** robot position (that is, $J$ is defined), this can only become true when the *end-effector* experiences a force equal to a desired force we assign to it.

Now, we can also design our **control law** to function with a **PD Controller**, allowing for greater control over its behavior. For our assumptions of the **system dynamics** $\tilde{\eta}$:
$$
\tau= \tilde{\eta}+J^T F_{EF}
$$
We design our control as:
$$
\tau= \tilde{\eta} + J^T (F_{D} + K_{P}\overbrace{ (F_{D} - F_{EF}) }^{ F_{e} } + 
K_{D}\overbrace{ (\dot{F}_{D} - \dot{F}_{EF}) }^{ \dot{F}_{e} }) 
$$
Substituting, we also cancel $\tilde{\eta}$.
$$
\cancel{ J^T } F_{EF} = \cancel{ J^T }(F_{D} + K_{P}F_{e} + K_{D}\dot{F}_{e})
$$
$$
\overbrace{ F_{D} - F_{EF} }^{ F_{e} } + K_{P}F_{e} + K_{D}\dot{F}_{e} = 0
$$
$$
(K_{P} - I)F_{e} + K_{D}\dot{F}_{e} = 0
$$
Assuming $K_{D}$ is **invertible**, we can rearrange some terms which leaves us an equation form very similar to a ***Lyapunov Equation***.
$$
\dot{F}_{E} = K_{D}^{-1} (K_{P} - I)F_{e} 
$$
$$
\dot{V} \leq -\alpha V
$$
Where we want to reduce the *error's velocity* towards 0.

```desmos-graph
left=-0.1; right=4;
top=4; bottom=-0.1;
---
f(x)=0.3
g(x)=3*1/ (e^x) |red|dashed
```

Unlike the graph, the **error's energy** wont just dissipate, but will oscillate under a zone (denoted by the blue line), this is due to the discrepancies between the **calculated** ***system's*** $\tilde{\eta}_{\tau}$ and the **real** $\tilde{\eta}$. If we include this in the equation, we get something similar to another ***Lyapunov Equation***.
$$
\dot{F}_{E} = K_{D}^{-1} (K_{P} - I)F_{e} +\underbrace{  \tilde{\eta} - \tilde{\eta}_{\tau} }_{ B }
$$
$$
\dot{V} \leq -\alpha V + \beta
$$
From our understanding of ***[[Lyapunov With Perturbations]]***, we now that we can limit this *oscillation zones* to be:
$$
\beta/\alpha
$$


#### Direct Force Control
TODAS LAS RESTRICCIONES APLICADAS AL VECTOR DE FUERZA PUEDEN SER ESCRITAS COMO RESTRICCIONES AL VECTOR DE VELOCIDAD DEL EFECTOR FINAL.