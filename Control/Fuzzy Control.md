---
tags:
  - ControlTheory
---
### By: ---
---
What is the difference between Classical and Fuzzy Set Theory?:: Fuzzy Set Theory deals with qualitative descriptions while Classical Set Theory deals more in absolutes.
<!--SR:!2024-11-13,55,310-->
What is Fuzzy logic used for?:: Too make decisions based on linguistics, which is often composed of vague concepts.
<!--SR:!2024-11-01,43,290-->
What is Fuzzification?:: Is the process of converting a real value of the universe of discourse to a value of a membership function. For $x=5$, $\mu_Ã(5)=0, \mu_\overset{\sim}{B}(5)=0.5,\mu_\overset{\sim}{C}(5)=0.7$ ![[Pasted image 20240822163500.png]]
<!--SR:!2024-10-26,37,290-->
What is a Singleton Fuzzy Set?:: A fuzzy set which is nonzero for all values except one.
<!--SR:!2024-10-03,14,296-->
What are some ways to define membership functions and which is the best?:: Asking the control/modeling expert to define them; Using data from the system to generate them; Trial & Error. Trial & Error tends to work the most effectively
<!--SR:!2025-05-30,66,276-->
What are some proposed Fuzzy logic operators
?
Zadeh AND:        $\mu_{\overset{\sim}{A}\bigcap \overset{\sim}{B}} = min(\mu_\overset{\sim}{A}(x),\mu_\overset{\sim}{B}(x))$
Product AND:     $\mu_{\overset{\sim}{A}\bigcap \overset{\sim}{B}} = \mu_\overset{\sim}{A}(x) \times \mu_\overset{\sim}{B}(x)$
Zadeh OR:          $\mu_{\overset{\sim}{A}\bigcup \overset{\sim}{B}} = max(\mu_\overset{\sim}{A}(x),\mu_\overset{\sim}{B}(x))$
Lukasiewicz OR: $\mu_{\overset{\sim}{A}\bigcup \overset{\sim}{B}} = min(\mu_\overset{\sim}{A}(x)+\mu_\overset{\sim}{B}(x), 1)$
<!--SR:!2024-08-27,1,236-->
What are fuzzy rules?:: Linguistic if-then statements involving fuzzy sets, logic and inference. They link input to output variables.
<!--SR:!2024-09-28,2,242-->
What are the major type of fuzzy rules?:: Mamdami and Takagi-Sugenor (TS).
<!--SR:!2024-10-09,13,282-->
What is fuzzy inference?:: Is what we use to calculate the output variables in the rule consequent. Mamdami and TS fuzzy rules use different methods of fuzzy inference.
<!--SR:!2024-09-28,1,202-->

