# Probability Notes
## Chapter 1
### Basic 
- Sample Space
    - Mutually exclusive
        Collectively exhaustive
    - Right granularity
- Event: Subset of the sample space
- Allocation of probabilities to events

1. $P(A) \gt 0$
2. $P(\Omega) = 1$ 
3. If $A \cap B  =  $, then $P(A \cup B) = P(A) + P(B)$  
### Uniform Law...
Discrete / Continuous
$$P(A) = \frac {number\\ of\\ elements\\ of\\ A} {total \\ number \\ of \\ sample\\ points} $$  
Counting or Area
### Conditional p and ...
$P(A|B) = \frac {P(A \cap B)} {P(B)}$, assuming $P(B) > 0$
- Multiplication rule:
$$P(A \cap B) = P(B) \cdot P(A|B) = P(A) \cdot P(B|A) $$
- Total Probability Theorem
$$P(B) = P(A) P(B|A) + P(A^c)P(B|A^c) $$
- Bayes Rule:
$$P(A_i|B) = \frac {P(A_i) P(B|A_i)} {P(B)}$$
### Independence
$P(B|A) = P(B)$ : "occurrence of A provides no information about B's occurrence"
=> Definition: $P(A \cap B) = P(A) \cdot P(B) $
Conditional independence, given C, is defined as independence under probability law $P(\cdot |C)$    
- Independence of a collection of events
    Events $A_1, A_2, \dots, A_n$ are called **independent** if:
$$ P(A_i \cap A_j \cap \cdots A_q) = P(A_i) P(A_j) \cdots P(A_q)$$ 
for any distinct indices $i, j, \dots, q$
Pairwise independence does not imply independence
### Counting... 
Principle: Discrete uniform law
**Permutations**: Number of ways of ordering *n* elements: $n!$
**Combinations**: number of k-element subsets of a given n-element set
$${n \choose k} = \frac {n!} {k!(n-k)!}$$
Binomial probabilities: P(k heads) = ${n \choose k} p^k (1-p)^{n-k}$

### Chapter 2 Discrete RV
### Random Variables
- Mathematically: A function from sample space $\Omega$ to the real numbers
    - discrete  or continuous values
random variable $X$, numerical value $x$
### Probability Mass Function
- Definition: Probability law/distribution of $X$,  $p_X(x) = P(X=x)$
- $p_X(x) \gt 0$ $\sum_x p_X(x) = 1$
geometric PMF: $p_X(k) = (1-p)^{k-1} p,  k = 1, 2, \dots$
binomial PMF: $p_X(k) = {n \choose k} p^k (1-p)^{n-k}$
### Expectation
- Definition: 
$$E[X] = \sum_x x p_X(x)$$
- Interpretations:
    - Center of gravity of PMF
    - Average in large number of repititions of the experiment
- Example: Uniform Distribution $[0, \dots, n]$, with expectation = $\frac n 2$
- Properties: $E[Y] = \sum_x g(x)p_X(x)$

### Variance
- Recall : $E[X^2] = \sum_x x^2 p_X(x)$
- Variance: 
$$var(x) = E[(X - E[X])^2] = \sum_x {(x - E[x])}^2 p_X(x) = E[X^2] - (E[X])^2$$
- Properties:
    - $var(X) \gt 0$
    - $var(\alpha X + \beta) = \alpha^2 var(X)$ 
### Conditional...Geometric...Joint
**Conditional PMF and expectation**
- $p_{X|A} (x) = P(X=x|A)$
- $E[X|A] = \sum_{x} x p_{X|A} (x)$
**Memoryless property** of Geometric PMF: Given that $X \gt 2$, the $r.v. X-2$ has the same geometric PMF
**Total Expectation theorem**
$$ p_X(x) = P(A_1) p_{X|A_1}(x) + \cdots + P(A_n)p_{X|A_n}(x)$$
$$ E[X] = P(A_1)E[X|A_1] + \cdots + P(A_n) E[X|A_n]$$
**Joint PMFs**:
- $p_{X,Y}(x, y) = P(X=x \\ and \\ Y=y)$
- marginal: $p_X(x) = \sum_y p_{X, Y}(x, y)$
- $p_{X|Y}(x|y) = P(X=x|Y=y) = \frac {p_{X,Y}(x,y)} {p_Y(y)}$
### MultiDRV: Exp, Cond, Indep
- Independent random variable: $p_{X, Y, Z} (x, y, z) = p_X(x) \cdot p_Y(y) \cdot p_Z(z)$
- Expectation: 
$$E[g(X, Y)] = \sum_x \sum_y g(x, y) p_{X, Y} (x, y)$$
- Variance: $Var(aX) = a^2 Var(X)$
- Example: **Binomial mean and variance**