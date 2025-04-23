#Chairing #Note
Being $q$ the joints such as:
$$
q = [q_{i}]_{i=1,\dots,n}
$$
The dynamic system is described as:
$$
M(q)\ddot{q} + C(q, \dot{q})\dot{q} + G(q) = \tau + \sum^p_{k=1} \lambda^T_{k} g_{k} (q)
$$
Where:
$$
q_{i}^- < q_{i} < q_{i}^+
$$
We want $\tau$ such that:
$$
\tau: \lvert \lvert q^* - q \rvert  \rvert \to 0, t\to \infty
$$

$$
\ddot{q}^* = h(t); q^* \in \mathbb{R}^n; q^* = [q_{i}^*]_{i=1,\dots,n}
$$
Where:
$$
q_{i}^- < q^* < q_{i}^+
$$
We also define the error as:
$$
\Delta =  q^* - q
$$
$$
\Delta_{i} = q_{i}^* - q_{i}
$$
So that:
$$
q_{i}^- - q_{i}^+ < \Delta_{i} < q_{i}^+ - q_{i}^-
$$
The asymmetric (considers both symmetric frontiers) Lyapunov function is:
$$
V(\Delta,\tilde{K}_{p},\tilde{K}_{D},t) =
\ln\left(  \prod^n_{i=1}  \left( \frac{ \Delta_{i}^+ }{ \Delta_{i}^+ - \Delta_{i} } \frac{- \Delta_{i}^- }{ \Delta_{i} + (-\Delta_{i}^-) } \right) \right) +
\left( \sum\left( (\frac{ q_{i}^+ }{ q_{i}^+ - q_{i} })^{-1} (\frac{ -q_{i}^- }{ q_{i} + (-q_{i}^-) })^{-1}  \right) \right) 
[tr\{ \tilde{K}_{p} K_{p}^T \} + tr \{ \tilde{K}_{D}\tilde{K}_{D}^T \}]
$$
