#PolePlacement #ControlTheory 
##### By Brian Douglas [Matlab]
---
LQR is a type of optimal controller that is based on the state-space representation.  We can compare it with a controller using [[Pole Placement]]. 

![[Pasted image 20240925115804.png]]

We observe how both of them are full state feedback controllers and have a similar structure. The main difference comes from one of the shortcomings of the [[Pole Placement]] method, which is how we can place the poles of our system wherever we want but, how do we know where is the best place to put them?

LQR helps us find the optimal $k$ by choosing characteristics based on performance and effort. We do this by defining a cost function that values certain characteristics above others, to help us find the optimal gains.

$$
J = \int_{0}^\infty (x^TQx + u^TRu)dt 
$$
Where:
$$
\begin{matrix}
Q = Performance-Gain \\
R = Effort-Gain 
\end{matrix}
$$
This cost function helps change more comprehensively the gains of our system based on qualities we desire from a system by simply changing the Q and R matrices. Rather than thinking on pole locations, we get to optimize based on the balance of performance and actuator effort we want.

We define the cost function as an integral to measure the area under the curve, as a bigger area means a worse performance (i.e. more time to reach a goal).

![[Pasted image 20241002121812.png]]

And then we square the states to only work with positive values, this also has the secondary effect of making it a quadratic function, which always has a definite minimum.

![[Pasted image 20241002121938.png]]

Matrices $Q$ and $R$ are both square with the same number of columns and rows as states in the system, and must be positive definite so that when multiplied by the state vectors:
$$x^TQx>0$$
It usually is a diagonal matrix that allows us to target certain states:
$$
\begin{bmatrix}
x_{1} & x_{2}  & \dots  & x_{n}  \\
\end{bmatrix}
\begin{bmatrix}
Q_{1} &  & & \dots \\
 & Q_{2} & \dots  &  \\
& \dots & \ddots & \\
\dots &  & & Q_{n}
\end{bmatrix}
\begin{bmatrix}
x_{1} \\
x_{2} \\
\vdots \\
x_{n}
\end{bmatrix}
$$
Augmenting each diagonal term penalizes error (with $Q$) on each state and extra actuator effort (with $R$) on each input. It is good practice for each term to be a multiple of 10.

Another less-common way to visualize the cost function is in the long matrix form:
$$
\begin{bmatrix}
x^T & u^t
\end{bmatrix}
\begin{bmatrix}
Q & 0 \\
0 & R
\end{bmatrix}
\begin{bmatrix}
x \\
u
\end{bmatrix}
$$
We observe how the diagonal values are the previously defined matrices, which each affect either the states or the input. But we also notice the off-diagonal terms, which in this case are zero, but we can also define as:

$$
\begin{bmatrix}
x^T & u^t
\end{bmatrix}
\begin{bmatrix}
Q & N \\
N^T & R
\end{bmatrix}
\begin{bmatrix}
x \\
u
\end{bmatrix}
$$
Where $N$ penalizes the cross product of $x$ and $u$.

We can easily implement LQR in Matlab using the `lqr()` function:
```
% System Dynamics
A = [0 1; 2 -1];
B = [1; 0];
C = [1 0];
D = 0;

% Control Law
Q = [1 0;
	 0 1];
R = 1;
K = lqr(A,B,Q,R);

$ Closed Loop System
sys = ss((A - B*k),B,C,D);
=======
% Closed Loop System
sys = ss((A - B*K),B,C,D);
>>>>>>> ebe038ba13857672f205e841c86df9370db924df
```

### Flashcards
---
What are the $Q$ and $R$ matrices and how do we define their values?:: $Q$ is the performance gain matrix, whose values are defined by augmenting the diagonal term that correspond to the states we wish to have a lower error faster; While $R$ is the actuator effort gain matrix, which we define by augmenting the diagonal values of the inputs that are more expensive.

How can we obtain the appropriate gains using the Linear Quadratic Regulator in Matlab?:: By defining the $Q$ and $R$ matrices and using the `lqr()` function.

