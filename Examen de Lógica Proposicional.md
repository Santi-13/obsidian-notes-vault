*Nombre: Santiago Peñúñuri Félix*
*Carrera (Institución): Ingeniería Mecatrónica*

---
1. (25 pts) Determinar la validez del siguiente argumento: 𝑝 → 𝑞, 𝑟 → 𝑞, 𝑟 ⊨ ¬$p$ 

| p   | r   | q   | $\neg p$ | $p \to q$ | $r \to q$ | $r ⊨ \neg p$ |
| --- | --- | --- | -------- | --------- | --------- | ------------ |
| V   | V   | V   | F        | V         | V         | F            |
| V   | V   | F   | F        | F         | F         | F            |
| F   | V   | V   | V        | V         | V         | V            |
| F   | V   | F   | V        | V         | F         | V            |
| V   | F   | V   | F        | V         | V         | V            |
| V   | F   | F   | F        | F         | V         | V            |
| F   | F   | V   | V        | V         | V         | F            |
| F   | F   | F   | V        | V         | V         | F            |

El argumento no es válido, ya que no sigue las premisas del argumento y hay casos en los que, aunque $p$ implique $q$ y $r$ implique $q$, $r$ no satisface $\neg p$.

---
2. (25 pts) Mostrar i) por tablas de verdad y ii) por algebra de proposiciones, si la expresión 𝑝 ↔ 𝑞 ≡ (𝑝 ∨ 𝑞) → (𝑞 ∧ 𝑝) es efectivamente una equivalencia.
i)

| $p$ | $q$ | $p \leftrightarrow q$ | $p ∨ q$ | $𝑞 ∧ 𝑝$ | $(𝑝 ∨ 𝑞) → (𝑞 ∧ 𝑝)$ | \*  |
| --- | --- | --------------------- | ------- | --------- | ----------------------- | --- |
| V   | V   | V                     | V       | V         | V                       | V   |
| V   | F   | F                     | V       | F         | F                       | V   |
| F   | V   | F                     | V       | F         | F                       | V   |
| F   | F   | V                     | F       | F         | V                       | V   |
\* la expresión entera

ii) 
$$p \leftrightarrow q \equiv (𝑝 ∨ 𝑞) → (𝑞 ∧ 𝑝)$$
$$
(p \to q) \wedge (q \to p) \equiv (p \vee q) \to (q \wedge p)
$$
$$
(\neg p \vee q) \wedge (p \vee \neg q) \equiv
$$

---
3. (25 pts) Resolver por resolución.
![[Pasted image 20250618113416.png]]
$\neg p \vee q$
$\neg q ∨ s$
$\neg r \vee s$
$\neg r \vee t$
$p \vee q ∨ r ∨ m$
---
$\therefore s ∨ t ∨ m$

Because:
$p \to q \equiv \neg p \vee q$

$s \vee s ∨ t ∨ m$
---
$\therefore s ∨ t ∨ m$

$s \vee q \vee r \vee m$
4. (20 pts) Considere la siguiente red.
![[Pasted image 20250618113424.png]]
Que puede representarse como (𝑝 ∨ 𝑞 ∨ 𝑟) ∧ (𝑝 ∨ 𝑡 ∨ ¬𝑞) ∧ (𝑝 ∨ ¬𝑡 ∨ 𝑟) Se propone la siguiente red como una solución equivalente mas sencilla como un mínimo de componentes.
![[Pasted image 20250618113435.png]]
¿Son las redes equivalentes? Justifique detalladamente su respuesta utilizando argumentos de lógica proposicional.

*Por leyes distributivas y conmutativas, se puede representar como:*
$$(𝑝 ∨ 𝑞 ∨ 𝑟) ∧ (𝑝 ∨ 𝑡 ∨ ¬𝑞) ∧ (𝑝 ∨ ¬𝑡 ∨ 𝑟)$$
$$p \vee [( q \vee r) \wedge ( t \vee \neg q ) \wedge ( \neg t \vee r )]$$
*Dando validez al camino de arriba de la propuesta. A su vez simplificamos lo de dentro.*
$$p \vee [( r \vee q ) \wedge ( r \vee \neg t ) \wedge ( t \vee \neg q ) ]$$
$$p \vee [ r \vee \underbrace{ (q \wedge \neg t) \cancel{ \wedge ( t \vee \neg q ) } }_{ \text{Son equivalentes, se simplifica} } ]$$
*Por lo que podemos concluir que la red propuesta es válida y tiene la solución más sencilla.*

5. (20 pts) Demostrar por inducción matemática que
![[Pasted image 20250618121542.png]]
Describa rigurosamente cada paso de la prueba de inducción.

