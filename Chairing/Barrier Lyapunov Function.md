#Explanation #Chairing 

***Barrier Lyapunov Functions*** (**BLF**) enforce **state constraints** by designing the ***Lyapunov Function*** $V_{B}$ to grow unbounded as $x$ approaches the constraint boundary, effectively making sure that the system ***never*** *violates constraints*. For our system, we define our **constraint** as:
$$
\mathrm{x} = \begin{bmatrix}
q \\
\dot{q}
\end{bmatrix}
$$
^6c6b52
$$
\lvert\lvert \mathrm{x} \rvert\rvert^2_{P} < x^+ 
$$
^0f3d2e
The constant $x^+$ is defined as the boundary of the state, in the case of two **cobots** working on the same **workspace**, this constant is constantly updated by the state of the other robot. This **dynamic constraint** is defined:
$$
\lvert\lvert \mathrm{x} \rvert\rvert^2_{P} < x^+ (\mathrm{x}_{j}), \text{ }\text{ }\text{ } i,j \in \{ 1,2 \}, \text{ }\text{ }\text{ } i \neq j
$$
Where $x^+(\mathrm{x}_{j})$ is updated based on the other robot's state to avoid collisions. 
#### Barrier Lyapunov Function
From our ***[[Euler-Lagrange Formulation]]***, we can get our *joints' acceleration* as:
$$
\ddot{q}= B^{-1}(q) (\tau-C(\dot{q},q) \dot{q} - G(q)) + B^{-1}\tau + \eta
$$
We can propose a **PD controller** that compensates for the dynamics such as:
$$
u= BK_{p}q + BK_{D} \dot{q} + C(q,\dot{q})\dot{q} + G(q) 
$$
After substituting, we get:
$$
\ddot{q} = K_{p}q + K_{D}\dot{q} + \eta
$$
Where $\eta$ represents **unmodeled dynamics/external perturbations**. In ***[[#^6c6b52|state-space form]]***:
$$
\dot{\mathrm{x}} = \begin{bmatrix}
0 & I \\
K_{p}  & K_{D}
\end{bmatrix} \mathrm{x} + \begin{bmatrix}
0 \\
I
\end{bmatrix} \eta
$$
$$
= A\mathrm{x} + B\eta
$$
#### Structure of BLF
The proposed *Barrier Lyapunov Function* is:
$$
V_{B} = \ln\left( \frac{ x^+ }{ x^+ - \lvert\lvert \mathrm{x} \rvert\rvert^2_{P} } \right) + \lambda_{1}(t)\text{tr}(\tilde{K}_{P} \tilde{K}_{P}^T) + \lambda_{2}(t) \text{tr}(\tilde{K}_{D} \tilde{K}_{D}^T)
$$
$\text{Where:}$
$\tilde{K}_{P} = K_{P} - K_{P}^0: \text{Proportional parameter estimation error}$.
$\tilde{K}_{D} = K_{D} - K_{D}^0: \text{Derivative parameter estimation error}$.
$\lambda_{1,2}(t): \text{Time-varying adaptive gains}$. 
$r: \text{Adjusts the decay rate of the decaying gain.}$

The logarithmic term $\ln\left( \frac{x^+}{x^+ - \lvert\lvert \mathrm{x} \rvert\rvert^2} \right)$ becomes singular as the *state* approaches the boundary $x^+$, ensuring our ***[[#^0f3d2e|boundary condition]]***. The ***[[Trace Operator|trace terms]]*** $\text{tr}(\tilde{K}_{P} \tilde{K}_{P}^T)$ & $\text{tr}(\tilde{K}_{D} \tilde{K}_{D}^T)$ are scalars penalizing **estimation errors** in the adaptive controller, and is equivalent to the ***[[Frobenius Norm|Squared Frobenius norm]]*** $\lvert\lvert \tilde{K}_{P} \rvert\rvert^2_{F}$.

The **adaptive gain term** $\lambda_{1,2}(t)$ is defined as:
$$
\lambda_{i} = \lambda_{i,0}\left( \frac{x^+ - \lvert\lvert \mathrm{x} \rvert\rvert^2_{P}}{x^+} \right)^r, r>0, i=1,2
$$
Where the exponent $r$ tunes how *sharply* adaptation **decays** near the *boundary*; and $\lambda_{i,0}$ represents a **constant** baseline **adaptation rate** for when the system **is far** from the *constraints*. Formally, as:
$$
\lvert\lvert \mathrm{x} \rvert\rvert^2_{P} \ll x^+
$$
Then:
$$
x^+ - \lvert\lvert \mathrm{x} \rvert\rvert^2_{P}  \approx 1
$$
So our term adapts **fully**:
$$
\lambda_{i}(t) \to \lambda_{i,0}⋅ 1^r = \lambda_{i,0}⋅
$$
On the contrary, when the system **approaches** the *constraint*:
$$
\lvert\lvert \mathrm{x} \rvert\rvert^2_{P} \to x^+
$$
Then:
$$
x^+ - \lvert\lvert \mathrm{x} \rvert\rvert^2_{P}  \to 0
$$
So adaptation is **suppressed** to prioritize **safety**:
$$
\lambda_{i}(t) \to \lambda_{i,0}⋅ 0^r = 0
$$
In summary:

| **State**               | **Distance to Boundary**     | **Adaptive Gain λi(t)λi​(t)** | **Barrier Term**          |
| ----------------------- | ---------------------------- | ----------------------------- | ------------------------- |
| **Far from constraint** | $x^+−∥\mathrm{x}∥_{P}^2≈x^+$ | $λ_{i}(t)≈λ_{i,0}$            | *Negligible* ($ln⁡(1)=0$) |
| **Near constraint**     | $x^+−∥\mathrm{x}∥_{P}^2→0$   | $λ_i(t)→0$                    | *Dominant* ($ln⁡(∞)$)     |
#### Derivative of the BLF
From its definition, its clear that the proposed ***BLF*** covers the first two requirements of any ***Lyapunov Function***. Now, its derivative is derived as follows:
$$
\frac{d}{dt} V_{B} = \frac{d}{dt} \ln\left( \frac{ x^+ }{ x^+ - \lvert\lvert \mathrm{x} \rvert\rvert^2_{P} } \right) + \frac{d}{dt} ( \lambda_{1}(t)\text{tr}(\tilde{K}_{P} \tilde{K}_{P}^T) ) + \frac{d}{dt} (\lambda_{2}(t) \text{tr}(\tilde{K}_{D} \tilde{K}_{D}^T))
$$
$\text{Where:}$
$$
\frac{d}{dt} \ln\left( \frac{ x^+ }{ x^+ - \lvert\lvert \mathrm{x} \rvert\rvert^2_{P} } \right) = \cancel{ \frac{d}{dt} \ln(x^+) } - \frac{d}{dt} \ln(x^+ - \lvert\lvert \mathrm{x} \rvert\rvert^2_{P}) 
$$
$$
= -\frac{1}{x^+ - \lvert\lvert \mathrm{x} \rvert\rvert^2_{P}} \frac{d}{dt} (\cancel{ x^+ } - \mathrm{x}^TP\mathrm{x})
$$
$$
= \frac{1}{x^+ - \lvert\lvert \mathrm{x} \rvert\rvert^2_{P}} + \dot{\mathrm{x}}^TP\mathrm{x}
$$
And given the derivative of the trace is:
$$
\frac{d}{dt} \text{tr}( \tilde{K}_{P} \tilde{K}_{P}^T ) = 2\text{tr}( \tilde{K}_{P}^T \dot{\tilde{K}_{P}}  )
$$
$$
\frac{d}{dt} ( \lambda_{1}(t)\text{tr}(\tilde{K}_{P} \tilde{K}_{P}^T) ) = 
$$