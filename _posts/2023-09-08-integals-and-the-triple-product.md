---
title: Integrals and the Jacobi Triple Product
# author: dxdydz
date: 2023-09-08 11:40:00 -0400
categories: [Calculus]
tags: [infinite products, infinite series, integration, contour integration, complex analysis]
math: True
pin: False
---

One of my favorite little oddities are integrals of infinite products. Definite integrals of infinite sums are *usually* straightforward but those of infinite products can be striking, in my opinion. How would one hope to evaluate an integral like

$$\int_0^1\prod_{n=1}^\infty(1-x^n)\,\mathrm dx?$$

The answer is to turn it into a series, of course!

## Product to sum identities

> **Theorem 1:** The Jacobi triple product
>
> $$\displaystyle{\prod_{n=1}^\infty(1-x^{2n})(1+x^{2n-1}z^2)(1+x^{2n-1}z^{-2})=\sum_{n=-\infty}^\infty x^{n^2}z^{2n}}$$
>
> $$\,$$

**Proof:** [See Wolfram.](https://mathworld.wolfram.com/JacobiTripleProduct.html) $\blacksquare$

Having worked so hard to establish the triple product identity, we can now move on to some special cases of it. In the Jacobi triple product, let $x\mapsto x^a$ and $z^2\mapsto-x^b$ to get

$$\prod_{n=1}^\infty(1-x^{2na})(1-x^{2na-a+b})(1-x^{2na-a-b})=\sum_{n=-\infty}^\infty(-1)^nx^{an^2+bn}.$$

Upon setting $a=3/2$ and $b=1/2$, we acquire the following well known result,

> **Theorem 2:** Euler's pentagonal number theorem
>
> $$\displaystyle{\prod_{n=1}^\infty(1-x^n)=\sum_{n=-\infty}^\infty(-1)^nx^{n(3n-1)/2}}$$
>
> $$\,$$

so-named because of the occurence of the pentagonal numbers, $n(3n-1)/2$. The product in the pentagonal number theorem is sometimes written as $\phi(x)$.

We may also acquire a similar identity involving the triangular numbers. Starting with the Jacobi triple product again, let $z^2\mapsto-xz$ so

$$\prod_{n=1}^\infty(1-x^{2n})(1-x^{2n}z)(1-x^{2n-2}z^{-1})=\sum_{n=0}^\infty(-1)^nx^{n^2+n}(z^n-z^{-n-1}).$$

Applying

$$\prod_{n=1}^\infty(1-x^{2n-2}z^{-1})=(1-z^{-1})\prod_{n=1}^\infty(1-x^{2n}z^{-1})$$

and

$$z^n-z^{-n-1}=(1-z^{-1})z^n(1+z^{-1}+z^{-2}+z^{-4}+\cdots+z^{-2n})$$

to the above yields

$$\prod_{n=1}^\infty(1-x^{2n})(1-x^{2n}z)(1-x^{2n}z^{-1})=\sum_{n=0}^\infty(-1)^nx^{n^2+n}z^n(1+z^{-1}+z^{-2}+z^{-4}+\cdots+z^{-2n}).$$

Letting $z=1$ and $x\mapsto x^{1/2}$ tells us that

$$\prod_{n=1}^\infty(1-x^n)^3=\sum_{n=0}^\infty(-1)^n(2n+1)x^{n(n+1)/2}$$

or written differently,

> **Corollary 1:**
>
> $$\displaystyle{\prod_{n=1}^\infty(1-x^n)^3=\sum_{n=-\infty}^\infty(-1)^nnx^{n(n+1)/2}.}$$
>
> $$\,$$

It's remarkable that if you cube $\phi(x)$, whose corresponding contains $x$ to the power of pentagonal numbers, that you get another sum which contains $x$ to the power of triangular numbers.

The last two product to sum idenities we need are comparatively simple, in the triple product we let $z=1$ and see that

> **Corollary 2:**
>
> $$\displaystyle{\prod_{n=1}^\infty(1+x^{2n-1})^2(1-x^{2n})=\sum_{n=-\infty}^\infty x^{n^2}.}$$
>
> $$\,$$

And for the very last time, in the triple product let $z\mapsto x$ and then make the change $x\mapsto x^{1/2}$, giving

> **Corollary 3:**
>
> $$\displaystyle{2\prod_{n=1}^\infty(1+x^n)^2(1-x^n)=\sum_{n=-\infty}^\infty x^{n(n+1)/2}.}$$
>
> $$\,$$

## Evaluating bilateral infinite series

Let $f(z)$ be a meromorphic with a finite set $S$ of poles $\zeta$ that are not integers. We will also restrict $f(z)$ to be a function such that there exists $k>1$ and a constant $M$ such that

$$|f(z)|<\frac{M}{|z|^k}.$$

When these conditions are met, we have

> **Theorem 3:**
>
> $$\displaystyle{\sum_{n=-\infty}^\infty f(n)=-\pi\sum_{\zeta\in S}\underset{z=\zeta}{\text{Res}}\left[f(z)\cot(\pi z)\right].}$$
>
> $$\,$$

This follows from evaluating the integral

$$I=\lim_{N\to\infty}\frac{1}{2\pi i}\oint_{C_N}\pi\cot(\pi z)f(z)\,\mathrm dz$$

in two ways. Here, $C_N$ is a square contour with vertices at $(N+1/2)e^{mi\pi/4}\sqrt{2}$ for $m=1,\,3,\,5,\,7$.

<center><a href="https://imgur.com/a/79yla3V"><img src="https://i.imgur.com/Yfe1q0C.png" alt="centered image" height="auto" width="367" title="source: imgur.com" /></a></center>

The first evaluation method is to employ the residue theorem to show that

$$I=\sum_{n=-\infty}^\infty f(n)+\pi\sum_{\zeta\in S}\underset{z=\zeta}{\text{Res}}\left[f(z)\cot(\pi z)\right],$$

and the second such method is by bounding the integrals along the edges of the square to show $I=0$. The details of the bounding argument may be seen [here](http://people.uncw.edu/hermanr/complex/summation-series-residue.pdf).

## The integrals

Integrating series term-by-term, applying summation by residues, and excising a lot of boring algebra yields the four integrals

$$\int_0^1\prod_{n=1}^\infty(1-x^n)\,\mathrm dx=\frac{4\pi\sqrt{3}}{\sqrt{23}}\cdot\frac{\text{sinh}\left(\frac{\pi\sqrt{23}}{3} \right )}{\text{cosh}\left(\frac{\pi\sqrt{23}}{2} \right )}$$

$$\int_0^1\prod_{n=1}^\infty(1-x^n)^3\,\mathrm dx=2\pi\text{sech}\left(\frac{\pi\sqrt{7}}{2}\right)$$

$$\int_0^1\prod_{n=1}^\infty(1+x^{2n-1})^2(1-x^{2n})\,\mathrm dx=\pi\coth(\pi)$$

$$\int_0^1\prod_{n=1}^\infty(1+x^n)^2(1-x^n)\,\mathrm dx=\frac{2\pi\tanh\left(\frac{\pi\sqrt{7}}{2}\right)}{\sqrt{7}}$$

which I was very happy to find as an undergrad! One of my professors found the values $\sqrt{23}$ and $\sqrt{7}$ appearing to be mysterious, as there's really no hint they should show up at all when looking at the integrand. In light of the prodcut to sum identities, the mystery reveals itself, as these numbers are related to the solutions of $1+z(3z-1)/2=0$ and $1+z(z+1)/2=0$, respectively.