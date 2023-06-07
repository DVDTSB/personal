---
title: "intro to induction"
category : "general-math"
tags : [induction]
---

# --work in progress--

## introduction

Mathematical induction is a a method of proving stuff by *recursion*, that is, proving a base case and then proving that if the statement is true for $n$ then it is true for $n+1$ (or similar variations).
This might seem a bit boring but it is actually very powerful and can be used to prove a lot of stuff.

## definition
> **Principle of Mathematical Induction**
> If we have an affirmation $P(n)$ that depends on a natural number $n$ and has the following properties:
> - $P(n_0)$ is true for some integer $n_0$ (this is called the base case)
> - If $P(n)$ is true then $P(n+1)$ is true (this is called the inductive step), sometimes this is replaced by $P(n)\implies P(n+1)$
> 
> Then $P(n)$ is true for all $n\geq n_0$.

The intuition behind this is that if we have a domino chain and we know that if one domino falls then the next one will fall too, and we push the first domino, then all the dominoes will fall or something like that.
Basically $P(n_0)\implies P(n_0+1)\implies P(n_0+2)\implies \cdots$

We can also do the same thing but in the other direction, for example if we have $P(n)\implies P(n-1)$, or use other variations like $P(n)\implies P(2n)$ or $P(n)\implies P(n^2)$.

## examples

> **Example 1** Prove that for any natural number $n$ we have 
> $$1+2+\cdots+n=\frac{n(n+1)}{2}$$

**Proof:** Let $P(n)$ be the statement $1+2+\cdots+n=\frac{n(n+1)}{2}$.
We will prove that $P(n)$ is true for all $n\geq 1$.

**Base case:** $P(1)$ is true because $1=\cfrac{1(1+1)}{2}$.

**Inductive step:** Suppose that $P(n)$ is true for some $n\geq 1$, then we have
$$1+2+\cdots+n+(n+1)=\frac{n(n+1)}{2}+(n+1)=\frac{n(n+1)+2(n+1)}{2}=\frac{(n+1)(n+2)}{2}$$
So $P(n+1)$ is true.
So by induction $P(n)$ is true for all $n\geq 1$.

That was kinda cool, but we can do better.






> **Example 2** Prove that for any natural number $n$ we have
> $$1^2+2^2+\cdots+n^2=\frac{n(n+1)(2n+1)}{6}$$

**Proof:** Let $P(n)$ be the statement $1^2+2^2+\cdots+n^2=\cfrac{n(n+1)(2n+1)}{6}$.
We will prove that $P(n)$ is true for all $n\geq 1$.

**Base case:** $P(1)$ is true because $1^2=\cfrac{1(1+1)(2\cdot 1+1)}{6}$.

**Inductive step:** Suppose that $P(n)$ is true for some $n\geq 1$, then we have
$$\begin{aligned}
1^2+2^2+\cdots+n^2+(n+1)^2&=\frac{n(n+1)(2n+1)}{6}+(n+1)^2\\\\
&=\frac{n(n+1)(2n+1)+6(n+1)^2}{6}\\\\
&=\frac{(n+1)(n(2n+1)+6(n+1))}{6}\\\\
&=\frac{(n+1)(2n^2+7n+6)}{6}\\\\
&=\frac{(n+1)(n+2)(2n+3)}{6}\\\\
&=\frac{(n+1)((n+1)+1)(2(n+1)+1)}{6}
\end{aligned}$$
So $P(n+1)$ is true.
So by induction $P(n)$ is true for all $n\geq 1$.

Other than weird identities like this, induction can be used to prove other stuff like inequalities.

> **Example 3** Prove that for any natural number $n\geq 5$ we have
> $$2^n>n^2$$

**Proof:** Let $P(n)$ be the statement $2^n>n^2$.
We will prove that $P(n)$ is true for all $n\geq 5$.

**Base case:** $P(5)$ is true because $2^5=32>25=5^2$.

**Inductive step:** Suppose that $P(n)$ is true for some $n\geq 5$, then we have
$$2^{n+1}=2\cdot 2^n>2n^2>n^2+2n+1=(n+1)^2$$
So $P(n+1)$ is true.
So by induction $P(n)$ is true for all $n\geq 5$.

> **Example 4**(Modulus Inequality) Prove that:
> $$|a_1+a_2+\cdots+a_n|\leq |a_1|+|a_2|+\cdots+|a_n|$$

**Proof:** Let $P(n)$ be the statement $|a_1+a_2+\cdots+a_n|\leq |a_1|+|a_2|+\cdots+|a_n|$.
We will prove that $P(n)$ is true for all $n\geq 1$.

**Base case:** $P(1)$ is true because $|a_1|=|a_1|$.
Also $P(2)$ is true because $|a_1+a_2|\leq |a_1|+|a_2|$.
**Inductive step:** Suppose that $P(n)$ is true for some $n\geq 1$, then we have
$$\begin{aligned}
|a_1+a_2+\cdots+a_n+a_{n+1}|&\leq |a_1+a_2+\cdots+a_n|+|a_{n+1}|\\\\
&\leq |a_1|+|a_2|+\cdots+|a_n|+|a_{n+1}|
\end{aligned}$$
Here we used $P(2)$ for the first inequality and $P(n)$ for the second inequality.
So $P(n+1)$ is true.
So by induction $P(n)$ is true for all $n\geq 1$.


