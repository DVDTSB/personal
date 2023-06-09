---
title:  "am-gm inequality"
categories : "algebra"
tags : [inequality, am-gm]
summary: "a short introduction to the am-gm inequality"
date: "2023-06-08"
---

## introduction
Before anything let's start with a basic fact:

>**Squares Lemma**
>$x^2\geq0$ for all real $x$, with equality $\iff x=0$

**Proof:** you can do it! i believe in you!


> **Definition of the Arihmetic Mean**
> The arihmetic mean of $x_1,x_2,\dots,x_n$ is equal to $$\frac{x_1+x_2+\cdots+x_n}{n}$$


> **Definition of the Geometric Mean**
> The arihmetic mean of $x_1,x_2,\dots,x_n$ is equal to $$\sqrt[n]{x_1 x_2 \cdots x_n}$$

## two variable AM-GM

Using the first fact we have:
$$(a-b)^2\geq 0 \iff a^2+b^2\geq 2ab$$

We just discovered:
> **Two Variable AM-GM Inequality**
> For any two positive reals $a$ and $b$ we have: $$\frac{a+b}{2}\geq \sqrt{ab}$$
> with equality $\iff a=b$

This is pretty nice actually, we can now prove a bunch of other things:
> **Example 1** Let $a$ be a positive real. Prove $$a+\frac{1}{a}\geq 2$$

**Proof:** By AM-GM we have $$a+\frac{1}{a}\geq 2\sqrt{a\cdot\frac{1}{a}}=2$$ with equality when $a=\cfrac{1}{a}\iff a=1$.

> **Example 2** Let $a,b,c$ be positive reals. Prove $$a^2+b^2+c^2 \geq ab+bc+ca$$
 
**Proof:** Notice that by AM-GM we have:
$$\frac{a^2+b^2}{2}\geq ab$$
$$\frac{b^2+c^2}{2}\geq bc$$
$$\frac{c^2+a^2}{2}\geq ca$$
By suming the above inequalities we get the desired result. Notice that the equality case for each of the above inequalities are $a=b, b=c, c=a \iff a=b=c$.

> **Example 3** Prove that for any positive reals $a,b$ we have $$a^4+b^4\geq a^3b+b^3a$$

**Proof:** Let's use AM-GM very carefully:

$$\begin{align}
a^4+b^4 & = \frac{a^4+b^4}{2}+\frac{a^4+b^4}{2} \\\\
& \geq \frac{a^4+b^4}{2}+a^2b^2 \\\\
& = \frac{a^4+a^2b^2}{2}+\frac{b^4+a^2b^2}{2} \\\\
& \geq a^3b+b^3a
\end{align}$$

## general AM-GM

> **General AM-GM Inequality**
> For the positive reals $x_1,x_2,\dots,x_n$ we have $$\frac{x_1+x_2 \cdots x_n}{n}\geq \sqrt[n]{x_1 x_2 \cdots x_n}$$
> with equality $\iff x_1=x_2=\cdots = x_n$

> **Example 4** Try to prove the case where $n=3$ and $n=4$ using basic AM-GM.

**Proof:** For $n=3$ we have $$a^3+b^3+c^3\geq 3abc \iff (a+b+c)(a^2+b^2+c^2-ab-bc-ca)\geq 0$$
inequality that is true because of *Example 2*.

For $n=4$ we have $$a^4+b^4+c^4+d^4\geq 2a^2b^2+2c^2d^2\geq 4abcd$$

> **Example 5** Show that for any positive reals $a,b,c$ we have: $$a^3+b^3+c^3\geq a^2b+b^2c+c^2a$$

**Proof:** We have by AM-GM the following inequalities:
$$\frac{a^3+a^3+b^3}{3}\geq a^2b$$
$$\frac{b^3+b^3+c^3}{3}\geq a^2b$$
$$\frac{c^3+c^3+a^3}{3}\geq a^2b$$
Adding the above inequalites we get the desired result.

As you can see terms with higher exponents are *stronger*, as they can *dominate* over the ones with smaller exponents, and that are more *mixed*.

Also, one last note, take note of the equality cases when using AM-GM. If you use AM-GM on let's say $x^2+1\geq 2x$ you are forcing equality when $x=1$. 

## exercises
>**Exercise 1** Find the maximum of $ab^3c^5$ if $a+b+c=12$.

>**Exercise 2** Let $n\geq 3$ be an integer and $x_1,x_2,\dots,x_n$ positive reals such that $x_1 x_2 \cdots x_n=1$. Prove that 
>$$(1+x_1)(1+x_2)^2\cdots (1+x_n)^n>n^n$$

>**Exercise 3** Show that for any positive reals $a,b,c$ we have: 
>$$\frac{a}{b}+\frac{b}{c}+\frac{c}{a}\geq 3$$

>**Exercise 4** Show that for any positive reals $a,b,c$ we have: 
>$$\frac{a}{b+c}+\frac{b}{c+a}+\frac{c}{a+b}\geq \frac{3}{2}$$

>**Exercise 5** Show that for any positive reals $a,b,c$ we have:
>$$\frac{a}{b}+\frac{b}{c}+\frac{c}{a}\geq \frac{a+b}{b+c}+\frac{b+c}{c+a}+\frac{c+a}{a+b}$$

I'll add more exercises later, quite lazy right now.