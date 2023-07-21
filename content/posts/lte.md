---
title: "we don't lift weights, we lift exponents"
date: 2023-07-21
tags: [lifting the exponent]
categories: "number theory"
summary: "a quick introduction to lifting the exponents lemma (lte)"
---

## introduction

Lifting the exponent is a kinda weird lemma, but it's quite useful when solving problems and Diophantine equations. It's pretty simple lmao.

I'll assume you are quite familiar with modular arithmetic, so if you aren't, go learn it (it's not that hard).

Btw everything is an integer.

## notation

Let's define $v_p(n)$ such that $p^{v_p(n)}\mid n$ and $p^{v_p(n)+1}\nmid n$. Aka the highest power of $p$ that divides $n$.

>**Example:** $v_2(12)=2$ because $2^2\mid 12$ and $2^3\nmid 12$.

This thing has some nice properties:

1. $p \nmid a \iff v_p(ab)=v_p(b)$
2. $v_p(ab)=v_p(a)+v_p(b)$
3. $a\mid b \implies v_p(a/b)=v_p(a)-v_p(b)$ 
4. $v_p(a+b)\geq \min(v_p(a),v_p(b))$
5. $v_p(gcd(a_1,a_2,\dots,a_n))=\min(v_p(a_1),v_p(a_2),\dots,v_p(a_n))$
6. $v_p(lcm(a_1,a_2,\dots,a_n))=\max(v_p(a_1),v_p(a_2),\dots,v_p(a_n))$
7. $v_p(n! )=\sum_{i=1}^{\infty} \left\lfloor \frac{n}{p^i} \right\rfloor$
8. $a\mid b \iff v_p(a)\leq v_p(b)\quad \forall p \text{ is prime}$ 
9. $a=b \iff v_p(a)=v_p(b)\quad \forall p \text{ is prime}$

>**Exercise:** Prove the above thingies.

For 7. one thing about the digits in base $p$.

>**Exercise:** Show that $gcd(a,b,c)=\frac{a\cdot b\cdot c \cdot lcm(a,b,c)}{lcm(a,b)\cdot lcm(b,c) \cdot lcm(c,a)}$

## Weak LTE

Let's start with some lemmas. I call these lemmas *Weak LTE* cuz they are weak and stuff.

>**Lemma 1:** Let $a,b$ be integers and $p$ a prime such that $p\mid a-b$ and $p\nmid a,b$. Let $n$ be a positive integer coprime with $p$. Then $$v_p(a^n-b^n)=v_p(a-b)$$

**Proof** We use:
$$ a^n-b^n=(a-b)(a^{n-1}+a^{n-2}b+\cdots+ab^{n-2}+b^{n-1})$$
We now need to show that $p \nmid a^{n-1}+a^{n-2}b+\cdots+ab^{n-2}+b^{n-1}$. Since we have $p\mid a-b$ we have $a \equiv b \pmod{p}$, so we have:

$$
\begin{align*}
a^{n-1}+&a^{n-2}b+\cdots+ab^{n-2}+b^{n-1} \\\\
 &\equiv a^{n-1}+a^{n-2}a+\cdots+aa^{n-2}+a^{n-1} \\\\
& \equiv na^{n-1} \\\\
& \not\equiv 0 \pmod{p}
\end{align*}
$$

>**Lemma 2:** Let $a,b$ be integers and $p$ a prime such that $p\mid a+b$ and $p\nmid a,b$. Let $n$ be an **odd** positive integer coprime with $p$. Then $$v_p(a^n+b^n)=v_p(a+b)+v_p(n)$$

**Proof** We use the fact that $n$ is odd, so $(-b)^n=-b^n$. From here just use the first lemma.

Yeah, that's it. You just kinda lift the exponent, make it go away, into the eternal void of nothingness.

## Strong LTE

Finally we have the strong LTE. This one is a bit more complicated, but it's still pretty simple.

>**Stronk LTE:** Let $a,b$ be integers and $p$ an **odd** prime such that $p\mid a-b$ and $p\nmid a,b$. Let $n$ be a positive integer. Then $$v_p(a^n-b^n)=v_p(a-b)+v_p(n)$$

**Proof** We will use induction on $v_p(n)$. We will first prove:
$$ v_p(a^p-b^p)=v_p(a-b)+1$$

Doing the same thing as before we have:
$$ a^p-b^p=(a-b)(a^{p-1}+a^{p-2}b+\cdots+ab^{p-2}+b^{p-1})$$
We will show that $v_p(a^{p-1}+a^{p-2}b+\cdots+ab^{p-2}+b^{p-1})=1$.
For this we need to show:
$$ p \mid a^{p-1}+a^{p-2}b+\cdots+ab^{p-2}+b^{p-1}$$
$$ p^2 \nmid a^{p-1}+a^{p-2}b+\cdots+ab^{p-2}+b^{p-1}$$

For the first part we have:
$$a^{p-1}+a^{p-2}b+\cdots+ab^{p-2}+b^{p-1}\equiv pa^{p-1} \equiv 0 \pmod{p}$$

For the second part we let $b=a+kp$. For a $t$ such that $1\leq t \leq p-1$ we have:
$$
\begin{align*}
b^t a ^{p-1-t} &\equiv (x+kp)^2+x^{p-1-t}\\\\
&\equiv x^{p-1-t}\left(x^t+tkpx^{t-1}+\frac{t(t-1)}{2}k^2p^2x^{t-2}+\cdots+k^p\right)\\\\
&\equiv x^{p-1-t}\left(x^t+tkpx^{t-1}\right)\\\\
&\equiv x^{p-1}+x^{p-1}tkp \pmod{p^2}
\end{align*}
$$

Using this we have:
$$
\begin{align*}
a^{p-1}+&a^{p-2}b+\cdots+ab^{p-2}+b^{p-1}  \\\\
&\equiv a^{p-1}+(a^{p-1}+kpa^{p-1})+...+(a^{p-1}+(p-1)kp x^{p-2}) \\\\
&\equiv pa^{p-1}+kp\frac{p(p-1)}{2}x^{p-2} \\\\
&\equiv pa^{p-1} \\\\
&\not\equiv 0 \pmod{p^2}
\end{align*}
$$

So $v_p(a^p-b^p)=v_p(a-b)+1$. 

Now we will prove the general case. Let $n=p^k m$ with $gcd(p,b)=1$. We have:

$$
\begin{align*}
v_p(a^n-b^n) &= v_p((a^{p^k})^m-(b^{p^k})^ m) \\\\
&= v_p(a^{p^k}-b^{p^k})= v_p((a^{p^{k-1}})^p-(b^{p^{k-1}})^p) \\\\
&= v_p(a^{p^{k-1}}-b^{p^{k-1}})+1 \\\\
&= v_p((a^{p^{k-2}})^p-(b^{p^{k-2}})^p)+1 \\\\
&= v_p(a^{p^{k-2}}-b^{p^{k-2}})+2 \\\\
&\quad \vdots \qquad (\text{do induction stuff}) \\\\
&= v_p(a-b)+k \\\\
&= v_p(a-b)+v_p(n)
\end{align*}
$$

>**Stronk LTE 2:** Let $a,b$ be integers and $p$ an **odd** prime such that $p\mid a+b$ and $p\nmid a,b$. Let $n$ be a positive integer. Then $$v_p(a^n+b^n)=v_p(a+b)+v_p(n)$$

**Proof.** Do the same things with the other lemma.

## $p-2$ thing

The nerds among you might whine about why did we assume $p$ is odd. TLDR: cuz we have a $\frac{p-1}{2}$ in the proof. However we can have something for $p=2$ too.

>**LTE for nerds***(case with $p=2$) Let $a,b$  be two **odd** integers with $4 \mid a-b$. We have:
$$ v_2(a^n-b^n)=v_2(a-b)+v_2(n)$$

**Proof** If $n$ is odd then use **Weak LTE**. Otherwise we have $n=2^k m$ with $m$ odd. We have again by **Weak LTE**:

$$v_2(a^n-b^n)=v_2((a^{2^k})^m-(b^{2^k})^m)=v_2(a^{2^k}-b^{2^k})$$

We need to show:
$$v_2(a^{2^k}-b^{2^k})=v_2(a-b)+k$$
We have:
$$ a^{2^k}-b^{2^k}=(a-b)(a+b)(a^2+b^2)(a^4+b^4)\cdots(a^{2^{k-1}}+b^{2^{k-1}})$$

Since $a \equiv b \equiv \pm 1 \pmod{4}$ we have $a^{2^i}+b^{2^i} \equiv 2 \pmod{4}$ for $i\geq 2$. So $v_2(a^{2^i}+b^{2^i})=1$ for $i\geq 2$. We also have $x+y \equiv 2 \pmod{4}$ for $x,y$ odd, so $v_2(a+b)=1$. So we have:
$$v_2(a^{2^k}-b^{2^k})=v_2(a-b)+v_2(a+b)+k-1=v_2(a-b)+k$$

>**LTE for Nerds** (episode 2) Let $a,b$ be two **odd** integers and let $n$ be an **even** integer. We have:
$$ v_2(a^n-b^n)=v_2(a-b)+v_2(a+b)+v_2(n)-1$$

**Proof** Since $a,b$ are odd we  have $4 \mid x^2-y^2$. Use this with the previous lemma.

## Cheat Sheet

Let $a,b$ be integers that are not multiples of $p$ and $n$ a positive integer. We have:

- if $p\neq 2$ and $p\mid a-b$ then $$v_p(a^n-b^n)=v_p(a-b)+v_p(n)$$
- if $p=2$ and $4\mid a-b$ then $$v_2(a^n-b^n)=v_2(a-b)+v_2(n)$$
- if $p=2$, $n$ is even and $2\mid a-b$ then $$v_2(a^n-b^n)=v_2(a-b)+v_2(a+b)+v_2(n)-1$$
- if $n$ is odd and $p\mid a+b$ then $$v_p(a^n+b^n)=v_p(a+b)+v_p(n)$$
- if $gcd(p,n)=1$ and $p\mid a-b$ then $$v_p(a^n-b^n)=v_p(a-b)$$
- if $n$ is odd, $gcd(p,n)=1$ and $p\mid a+b$ then $$v_p(a^n+b^n)=v_p(a+b)$$

**ALWAYS CHECK IF THE CONDITIONS ARE SATISFIED, DONT FORGET TO CHECK IF $p\mid a-b$ OR $p\mid a+b$**
**ALSO DON'T FORGET THE CASE $p=2$**



