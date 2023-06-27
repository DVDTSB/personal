---
title: "intro to induction"
categories : "general-math"
tags : [induction, inequality]
summary: "a short introduction to mathematical induction"
date: "2023-06-09"
---


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

> **Example 4** (Modulus Inequality) Prove that:
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

## am-gm proof 1

> **Example 5** Prove that for any positive real numbers $a_1,a_2,\dots,a_n$ we have
> $$\frac{a_1+a_2+\cdots+a_n}{n}\geq \sqrt[n]{a_1a_2\cdots a_n}$$

**Proof:** Since the inequality is homogeneous, we can assume that $a_1 a_2 \cdots a_n=1$.

We have to prove that $a_1+a_2+\cdots+a_n\geq n$. We will prove this by induction.

Let $P(n)$ be the statement $a_1+a_2+\cdots+a_n\geq n$.

**Base case:** $P(2)$ is true because 
$$a_1+a_2\geq 2\sqrt{a_1a_2} \iff (\sqrt{a_1}-\sqrt{a_2})^2\geq 2$$

**Inductive step:** Suppose that $P(n)$ is true for some $n\geq 2$, we will prove that $P(n+1)$ is true.
We have to prove 
$$a_1+a_2+\cdots+a_n+a_{n+1}\geq n+1$$
But we know that since $a_1 a_2 \cdots a_n=1$ we have two numbers $a_i$ and $a_j$ such that $a_i\geq 1$ and $a_j\leq 1$. Let $i=1$ and $j=2$ for example. Then we have 
$$a_1 a_2 +1 \leq a_1 + a_2 \iff (a_1 - 1)(a_2-1)\leq 0$$
So we have
$$a_1+a_2+\cdots+a_n+a_{n+1}\geq 1+a_1 a_2 + a_3 + \cdots a_n + a_{n+1}$$
Making the substitution $a_1 a_2=a$ we have to prove
$$1+a+a_3+\cdots+a_n+a_{n+1}\geq n+1 \iff a+a_3 + \cdots a_n + a_{n+1} \leq 1$$
And that is just $P(n)$, since the product is still 1, so we are done.
## strong induction

Sometimes we need to use a stronger version of induction, which is called strong induction (i wonder why). The difference is that in strong induction we assume that $P(1),P(2),\cdots,P(n)$ are all true, and we use this to prove that $P(n+1)$ is true. This is useful when we need to use more than one base case.

> **Example 5** Prove that if $x+y$, $x^2+y^2$, $x^3+y^3$ and $x^4+y^4$ are all integers, then $x^n+y^n$ is an integer for all $n$ positive integers.

**Proof:** Notice that $(x+y)^2=x^2+2xy+y^2$ is an integer, so $2xy$ is an integer, so $xy=\cfrac{k}{2}$ for some integer $k$.
Furthermore $(x^2+y^2)^2=x^4+2x^2y^2+y^4$ is an integer, so $2x^2y^2$ is an integer, so $\cfrac{k^2}{4}$ is an integer, so $k^2$ is divisible by $4$, so $k$ is divisible by $2$. So $xy$ is an integer.

Let $P(n)$ be the statement $x^n+y^n$ is an integer.
We will prove that $P(n)$ is true for all $n\geq 1$.

**Base case:** $P(1)$ is true because $x+y$ is an integer.
Also $P(2)$ is true because $x^2+y^2$ is an integer.

**Inductive step:** Suppose that $P(1),P(2),\cdots,P(n)$ are all true for some $n\geq 2$, then we have
$$x^{n+1}+y^{n+1}=(x+y)(x^n+y^n)-xy(x^{n-1}+y^{n-1})$$
So since $x+y$, $x^n+y^n$ and $xy$ are all integers, $x^{n+1}+y^{n+1}$ is an integer.
So $P(n+1)$ is true.
So by induction $P(n)$ is true for all $n\geq 1$, weee.

## cauchy induction

Since everything sounds cooler when you add *Cauchy* before it, we of course also have Cauchy Induction. Here if the affirmation $P(n)$, with $n\in\mathbb{N}$ has the following properties:
- $P(n_1)$ is true for a certain $n_1$.
- $P(kn)$ is true for if $P(n)$ is true, for a constant $k\in \mathbb{N}$.
- $P(n-1)$ is true if $P(n)$ is true.

Then $P(n)$ is true for all $n$.


> **Exercise** Try to prove AM-GM using Cauchy Induction.


## exercises

> **Exercise 1** Let $x_1=1$ and $x_{n+1}=x_n+\cfrac{1}{x_n}$ for all $n\geq 1$. Prove that $\cfrac{3\sqrt{n}}{2}\geq x_n \geq 2 \text{for all } n\geq 1$
