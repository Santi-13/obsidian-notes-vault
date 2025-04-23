#Chairing #Note
To the system dynamics we add the uncertainty $v$:
$$
\dot{q}=Aq+v
$$
Example.
$$
\lvert \lvert v \rvert  \rvert \leq v^+\lvert \lvert q \rvert  \rvert  
$$
For the lyapunov function:
$$
V(q) = \frac{1}{2} \lvert \lvert q \rvert  \rvert^2_{P}=\frac{1}{2} q^T Pq 
$$

The time derivative of $V(q)$ satisifies:
$$
\frac{d}{dt} V(q)= q^T P \frac{d}{dt}q 
$$
$$
=q^TP(Aq+v)
$$
$$
= q^TPAq+q^TPv
$$
As we don't exactly know the values of $v$, we can express them in terms of their limits.
#### Multiplicative Form
$$
q^TPv \leq \lvert \lvert Pq \rvert  \rvert \text{ }\lvert \lvert v \rvert  \rvert 
\leq v^+ \lvert \lvert P \rvert  \rvert_{F}  \lvert \lvert q \rvert  \rvert^2 
$$
$$
\leq v^+ \lvert \lvert P \rvert  \rvert_{F} \text{ } q^Tq
$$
$$
= q^T(v^+ \lvert \lvert P \rvert  \rvert I_{n})q
$$
Hence:
$$
\frac{d}{dt} V(q) \leq \frac{1}{2} q^T(PA+A^TP+Q_{0})q
$$
$$
Q_{0}=2v^+ \lvert \lvert P \rvert  \rvert I_{n} 
$$
Then if:
$$
PA+A^T+P+Q_{0}\leq -Q,\dots Q>0
$$
Results in:
$$
\frac{d}{dt} V(q) \leq -\frac{1}{2} q^T Qq\leq 0
$$

#### Additive Form
$$
\frac{d}{dt} V(q)= q^T P \frac{d}{dt}q 
$$
$$
=q^TP(Aq+v)
$$
$$
= q^TPAq+q^TPv
$$
We can use the Peter-Paul inequality to decouple the uncertainty from the dynamics of the system. The theorem is as follows:
$$
x^T y \leq (1+\theta) \lvert \lvert x \rvert  \rvert^2+(1-\theta^{-1})\lvert \lvert y \rvert  \rvert^2,\dots x,y \in \mathbb{R}^n,\theta \in \mathbb{R}^+  
$$

Then if $q^TP=x^T$, and $v=y$, then:
$$
q^T Pv \leq (1+\theta) \lvert \lvert Pq \rvert  \rvert^2+(1-\theta^{-1})\lvert \lvert v \rvert  \rvert^2
$$
$$
=q^TP((1+\theta)I_{n})Pq + (1+\theta^{-1})(v^+)^2
$$
Hence:
(got lost)

Find the derivative of $V(t)$.

---
We can define the square root of a matrix in two different ways:
1. $$
P^{1/2} : P^{1/2}+P^{1/2}=P
$$
2. Choleski $$
P^{1/2}=\bar{P}: \bar{P}^T\bar{P}=P
$$

