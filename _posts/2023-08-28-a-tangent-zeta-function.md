---
title: A Tangent "Zeta Function"
# author: dxdydz
date: 2023-08-28 15:15:00 -0400
categories: [Calculus]
tags: [complex analysis, infinite series, infinite products, generating functions, differential equations]
math: True
pin: False
---

Let the sequence $\left\\{x_n\right\\}_{n=1}^\infty$ be the positive solutions to $\tan(x)=x$ ordered by increasing magnitude and define the function

$$\zeta_t(s)=\sum_{n=1}^\infty\frac{1}{x_n^s}.$$

It is not hard to show that $\zeta_t(s)$ converges for $\Re(s)>1$. Also consider the function

$$f(x)=\frac{\sin(x)}{x}-\cos(x)$$

which has the same solutions as $\tan(x)=x$ (excluding $x=0$) and admits the Weierstrass factorization

$$f(z)=\frac{z^2}{3}\prod_{n=1}^\infty\left(1-\frac{z^2}{x_n^2}\right).$$

Taking the logarithmic derivative of the above product, applying the geometric series, and interchanging the order of the resulting sums yields the generating function

$$-\frac{z^2}{2(1-z\cot(z))}+\frac{3}{2}=\sum_{n=1}^\infty\zeta_t(2n)z^{2n}.\tag{1}$$

Applying the Cauchy product to $(1)$ and comparing like powers of $z$ gives the recurrence relation

$$\zeta_t(2n+2)=9\frac{\zeta(2n+4)}{\pi^{2n+4}}-6\sum_{k=0}^{n-1}\frac{\zeta_t(2k+2)\zeta(2n-2k+2)}{\pi^{2n-2k+2}},\qquad n\geq0$$

where $\zeta(s)$ is the Riemann zeta function. This allows us to calculate $\zeta_t(2n)$ for $n\geq1$, for example, the first few such values are as follows.

| $n$ | $\zeta_t(2n)$ |
| --- | --- |
| $1$ | $1/10$ |
| $2$ | $1/350$ |
| $3$ | $1/7875$ |
| $4$ | $37/6063750$ |
| $5$ | $59/197071875$ |
| $6$ | $2753/186232921875$ |

A much nicer recurrance in the form of a convolution identity can be established by noting that the function in $(1)$ is a solution to the Riccati equation

$$zy'(z)-\frac{z^2}{2}+\frac{9}{8}=2y^2(z).$$

Plugging in $y(z)=-z^2/(2(1-z\cot(z)))+3/2$ and applying Cauchy convolution again gives the much nicer relation

$$\zeta_t(2n)=\frac{1}{n+\frac{3}{2}}\sum_{k=1}^{n-1}\zeta_t(2k)\zeta_t(2n-2k).\tag{2}$$

## A little conjecture

Both $(1)$ and $(2)$ compare quite nicely with the similar identities

$$-\frac{\pi z}{2}\cot(\pi z)+\frac{1}{2}=\sum_{n=1}^\infty\zeta(2n)z^{2n}\tag{3}$$

and

$$\zeta(2n)=\frac{1}{n+\frac{1}{2}}\sum_{k=1}^{n-1}\zeta(2k)\zeta(2n-2k)\tag{4}$$

for the Riemann zeta function. Notably, we also have the well known fact that $\zeta(0)=-1/2$ and we see this special value show up in $(3)$ and $(4)$. In a similar manner, the value $-3/2$ appears in the same spots in the equations for $\zeta_t(s)$. So it seems reasonable to conjecture that, upon analytic continuation, we'd have $\zeta_t(0)=-3/2$.

## Some additional thoughts

Originally, I tried to prove this using the asymptotic method outlined in a paper on the Casimir effect inside of sphere[^1], but this proved unsucessful due to the poles of $y(z)$ along $\mathbb{R}^+$ and other unfortunate asymptotic behavior. Another idea that ended up not being fruitful was to rotate $y(z)$ into $y(iz)$ and integrate that instead, as done in [this similar problem](https://math.stackexchange.com/questions/2012717/mellin-transform-of-the-tan-function) on math.se.

This led me to consider the *possible* identities

$$\int_0^\infty\left(-\frac{x^2}{2(x\coth(x)-1)}-\frac{x^2}{2(1-x)}+\frac{1}{2(1-x)}\right)x^{s-1}\,\mathrm dx\overset{\text{?}}{=}\frac{\pi\zeta_t(-s)}{\sin(\pi s)}$$

or

$$\frac{\sin(\pi s)}{\pi}\left(\int_0^\infty\left(f_1(x)-f_2(x)\right)x^{s-1}\,\mathrm dx+\alpha\Gamma(s)\right)\overset{\text{?}}{=}\zeta_t(-s)$$

where

$$f_1(x)=-\frac{x^2}{2(x\coth(x)-1)}$$

and

$$f_2(x)=-\frac{3}{2}e^{-x}+\frac{x^2}{2(1-x)}-\frac{1}{2(1-x)}$$

with the intention that the second integral is only valid for $\alpha=-3/2$. The hope here is that they could possibly have been given some numerical evidence. Unsuprisingly, neither of these integral identities actually worked out numerically, as they are acquired by formal manipulation only without regard to important unknown information about $\zeta_t(s)$, such as the loactions of possible poles. There is also th issue that I couldn't find a way to use Ramanujan's master theorem in quite the way I wanted to. Perhaps these approaches could be modified to work in some way that I do not see, and if not, these methods could at least be avoided by anyone that takes a stab at this.

## References

[^1]: *Bessel &#950;-function approach to the Casimir effect of a scalar field in a spherical bag*, August Romeo, [https://journals.aps.org/prd/abstract/10.1103/PhysRevD.52.7308](https://journals.aps.org/prd/abstract/10.1103/PhysRevD.52.7308)