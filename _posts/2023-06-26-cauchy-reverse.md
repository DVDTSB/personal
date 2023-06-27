---
title: "cauchy reverse"
category : "algebra"
tags : [inequality, cauchy, am-gm]
---

# -work in progress-

## notation

So there are going to be a bunch of sums here, so we will use the cyclic sum notation. Basically, we cycle trough all the variables or something. Here is an example:
$$\sum_{cyc} a^3b^2c=a^3b^2c+b^3c^2a+c^3a^2b$$
You get it right?

## introduction
Yeah so I have no idea why this technique is called "Cauchy Reverse", since it doesn't really have anything to do with the Cauchy-Schwarz inequality, but whatever. This technique is very useful for proving inequalities, and it's pretty simple to use. 

I'm not really sure how to explain this, so I'll just start with a simple inequality to see where the motivation comes from.

> **Example 1** Let $a,b,c$ be positive reals with sum 3. Prove 
> $$ \frac{1}{a^2+1}+\frac{1}{b^2+1}+\frac{1}{c^2+1}\geq \frac{3}{2}$$

**Proof:** Notice that $a^2+1\geq 2a$ by AM-GM, so it would be quite nice to, you know, get rid of the $a^2+1$ in the denominator. Sadly we can't do that because of the sign. So what if, you know, we flip the sign. So we multiply both sides by $-1$ and get:
$$ -\sum_{cyc}\frac{1}{a^2+1}\leq \frac{-3}{2}$$

However $-\cfrac{1}{a^2-1}$ is negative, so we can't use AM-GM. But what if we add $3$ to both sides? We get:

$$ 3-\sum_{cyc}\frac{1}{a^2+1}\leq \frac{3}{2} \Longleftrightarrow
\sum_{cyc}\frac{a^2}{a^2+1}\leq \frac{3}{2}$$

Now we can use AM-GM like we planned to we have:

$$ \sum_{cyc}\frac{a^2}{a^2+1}\leq \sum_{cyc}\frac{a^2}{2a} = \frac{a+b+c}{2} = \frac{3}{2}$$

Pretty cool, indeed.

So you can see from where the "reverse" part of the name comes from. Now let's see more examples.

> **Example 2** Let $a,b,c$ be positive reals with sum 3. Prove
> $$ \frac{b}{a^2+1}+\frac{c}{b^2+1}+\frac{a}{c^2+1}\geq \frac{3}{2}$$
**Proof:** So same thing here, except we got each term multiplied by a variable. Trying the same thing as before, we get:
$$ 3- \sum_{cyc}\frac{b}{a^2+1}=\sum_{cyc}\frac{a^2+1-b}{a^2+1}$$
And this looks pretty bad (because it is). However, instead of subtracting each term from a $1$, why don't we try to see what happens if we subtract it from a constant $k$? So we get:
$$ k - \frac{b}{a^2+1}=\frac{ka^2+k-b}{a^2+1}$$
Well, not let's try to choose the constant $k$ to make things clear out. Clearly $k=b$ works, so we get:
$$ b - \frac{b}{a^2+1}=\frac{ba^2+b-b}{a^2+b}=\frac{a^2b}{a^2+1}\leq \frac{a^2b}{2a}=\frac{ab}{2}$$
That made things pretty nice. Using this we have to prove:
$$ (a+b+c)- \frac{b}{a^2+1}\sum_{cyc}\leq -\frac{3}{2}+(a+b+c)=\frac{3}{2}$$
And 
$$ (a+b+c)- \sum_{cyc}\frac{b}{a^2+1}= \sum_{cyc}\frac{a^2b}{a^2+1}\leq \frac{ab+bc+ca}{2}$$

So we have to prove:
$$ ab+bc+ca \leq 3 \Longleftrightarrow ab+bc+ca\leq a^2+b^2+c^2$$
Obvious by AM-GM.