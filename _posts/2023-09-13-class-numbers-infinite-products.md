---
title: Dirichlet's Class Number Formula and Infinite Products
# author: dxdydz
date: 2023-09-13 11:00:00 -0400
categories: [Number Theory]
tags: [algebraic number theory, infinite products, infinite series]
math: True
pin: False
---

Some time ago I was messing around and brewed up a cute little Wallace-type product for the golden ratio,

$$\begin{align*}\phi=\frac{2\cdot3}{1\cdot4}\cdot\frac{7\cdot8}{6\cdot9}\cdot\frac{12\cdot13}{11\cdot14}\cdot\frac{17\cdot18}{16\cdot19}\cdot\frac{22\cdot23}{21\cdot24}\cdots.\tag{1}\end{align*}$$

At first glance this identity is pretty mundane, but there's something very odd about it &#8212; all of the denominator terms are quadractic residues mod $5$ and all of the numerator terms are quadratic non-residues mod $5$. Perhaps a proof of this product will shed light on why this is happening.

**Proof of (1):** We can start with the fact that $2\cos\left(\frac{\pi}{5}\right)=\phi$, which implies $\frac{\sin\left(2\pi/5\right)}{\sin\left(\pi/5\right)}=\phi$. Applying Euler's product for the sine yields

$$\begin{align*}\frac{\sin\left(\frac{2\pi}{5} \right )}{\sin\left(\frac{\pi}{5} \right )} &=\frac{\frac{2\pi}{5}\prod_{n=1}^\infty\left(1-\frac{(2\pi/5)^2}{n^2\pi^2} \right )}{\frac{\pi}{5}\prod_{n=1}^\infty\left(1-\frac{(\pi/5)^2}{n^2\pi^2} \right )} \\ &=2\prod_{n=1}^\infty\frac{(5n)^2-4}{(5n)^2-1} \\ &= 2\prod_{n=1}^\infty\frac{(5n+2)(5n-2)}{(5n+1)(5n-1)}\\ &= \prod_{n=0}^\infty\frac{(5n+2)(5n+3)}{(5n+1)(5n+4)}.\qquad\blacksquare\\\end{align*}$$

Nice and easy, but no real insight into why this pattern occurs.
 
## A class number formula
 
It was not until much later that I realized this product could be obtained through a special case of the Dirichlet class number formula. Let $\chi(n)=\left(\frac{d}{n}\right)$  where $\left(\frac{d}{n}\right)$ is the Kronecker symbol associated to a real quadratic field $\mathbb{Q}(\sqrt{d})$. Also suppose the shortest period of $\chi(n)$ is a prime $p\equiv1\,(\text{mod}\,4)$, then

$$\begin{align*}\sum_{n=1}^\infty\frac{\chi(n)}{n}=-\frac{1}{2\sqrt{p}}\sum_{n=1}^{p-1}\left(\frac{n}{p}\right)\ln\left(\sin\left(\frac{n\pi}{p}\right)\right).\tag{2}\end{align*}$$


We also have

$$h(d)=\frac{\sqrt{d}}{\ln(\epsilon)}\sum_{n=1}^\infty\frac{\chi(n)}{n}$$

where $h(d)$ is the class number of $\mathbb{Q}(\sqrt{d})$ and $\epsilon$ is the fundamental unit of the same field. Combing this with $(2)$ tells us that

$$\begin{align*}\frac{h(d)\ln(\epsilon)}{\sqrt{d}}=-\frac{1}{2\sqrt{p}}\sum_{n=1}^{p-1}\left(\frac{n}{p}\right)\ln\left(\sin\left(\frac{n\pi}{p}\right)\right).\end{align*}$$

Now pick $d$ such that $h(d)=1$ and $p=d,$ then upon exponentiating the above we see that

$$\epsilon=\prod_{n=1}^{p-1}\left(\sin\left(\frac{n\pi}{p}\right)\right)^{-(n\,|\,p)/2}$$

and if we make use of some basic symmetry of the sine function we get

$$\begin{align*}\epsilon=\prod_{n=1}^{(p-1)/2}\left(\sin\left(\frac{n\pi}{p}\right)\right)^{-(n\,|\,p)}.\tag{3}\end{align*}$$

So now we see how the factors were distributed by residues!

## Acquiring new products

Using $(3)$ in combination with $\sin(n\pi/p)=\Gamma(n/p)\Gamma(1-n/p)$ and

$$\prod_{m=1}^k\frac{\Gamma(1-b_m)}{\Gamma(1-a_m)}=\prod_{n=1}^\infty\prod_{m=1}^k\frac{n-a_m}{n-b_m}$$

where $b_m\notin\mathbb{N}$ for all $m$ and $\sum_{m=1}^k(a_m-b_m)=0$ lets us quickly churn out a bunch of these products. As a quick note before we proceed, the fundamental unit, $\epsilon=\frac{x_0+y_0\sqrt{d}}{2}$, may be calculated by finding the smallest positive integer solution $(x_0,\,y_0)$ to $x^2-dy^2=\pm4.$ And we can easily pick out fields wth class number $1$ with any old table.

### $\mathbb{Q}(\sqrt{5})$

In this field, when $d=5$, we have $p=5$, $h(5)=1$, and $\epsilon=\frac{1+\sqrt{5}}{2}$. Using these in $(3)$ produces $(1)$.

### $\mathbb{Q}(\sqrt{13})$

Here we have $p=13$, $h(13)=1$, and $\epsilon=\frac{3+\sqrt{13}}{2}$ so

$$\frac{3+\sqrt{13}}{2}=\prod_{n=0}^\infty\frac{(13n+2)(13n+5)(13n+6)(13n+7)(13n+8)(13n+11)}{(13n+1)(13n+3)(13n+4)(13n+9)(13n+10)(13n+12)}.$$

### $\mathbb{Q}(\sqrt{29})$

Setting $d=29$ has $p=29$, $h(29)=1$, and $\epsilon=\frac{5+\sqrt{29}}{2}$ which leads us to the gargantuan product

$$\frac{5+\sqrt{29}}{2}=\prod_{n=0}^\infty\frac{(29n+2)(29n+3)(29n+8)(29n+10)(29n+11)(29n+12)(29n+14)(29n+15)(29n+17)(29n+18)(29n+19)(29n+21)(29n+26)(29n+27)}{(29n+1)(29n+4)(29n+5)(29n+6)(29n+7)(29n+9)(29n+13)(29n+16)(29n+20)(29n+22)(29n+23)(29n+24)(29n+25)(29n+28)}.$$

And that will be the last one because things are starting to get hideous.

## Algebraic gamma quotients

Another way to generalize this is by asking: when is a quotient of gamma functions algebraic? Playing around with the reflection formula, minimal polynomials, and some educated guesses gave the value

$$\frac{\Gamma\left(\frac{1}{24}\right)\Gamma\left(\frac{11}{24}\right)}{\Gamma\left(\frac{5}{24}\right)\Gamma\left(\frac{7}{24}\right)}=\sqrt{3}\sqrt{3+\sqrt{2}}$$

which satisfies $x^4-12x^2+9=0$. Not to my surprise, this was already listed [on Wolfram](http://mathworld.wolfram.com/GammaFunction.html). Some browsing on stack exchange also turns up [the remarkable identity](https://math.stackexchange.com/questions/3041736/how-to-derive-the-closed-form-of-this-gamma-quotient)

$$\frac{\Gamma\left(\frac{1}{21}\right)\Gamma\left(\frac{4}{21}\right)\Gamma\left(\frac{16}{21}\right)}{\Gamma\left(\frac{2}{21}\right)\Gamma\left(\frac{8}{21}\right)\Gamma\left(\frac{11}{21}\right)}=\sqrt[3]{14+3\sqrt{21}}$$

conjectured by user Wolfgang and proven by pisco by making use of the Gauss multiplication formula for the gamma function.