---
title: On Combinatorics and Contours
# author: dxdydz
date: 2023-10-04 11:00:00 -0400
categories: [Calculus]
tags: [integration, infinite series, contour integrals, combinatorics]
math: True
pin: False
---

Consider the contour integral

$$\frac{1}{2\pi i}\oint_C\frac{(1+z)^n}{z^{k+1}}\,\mathrm dz$$

where $C$ is a positively oriented circular contour centered at $z=0$. If we expand the term in the numerator using the binomial theorem, we see that the above integral is

$$\frac{1}{2\pi i}\oint_C\left(\binom{n}{0}+\cdots+\binom{n}{k-1}z^{k-1}+\binom{n}{k}z^k+\binom{n}{k+1}z^{k+1}+\cdots+\binom{n}{n}z^n\right)\frac{1}{z^{k+1}}\,\mathrm dz.$$

The coeffcient of the $1/z$ term is $\binom{n}{k}$, so it follows that

$$\frac{1}{2\pi i}\oint_C\frac{(1+z)^n}{z^{k+1}}\,\mathrm dz=\binom{n}{k}.$$

The use of this contour integral &#8212; and similar integrals &#8212; to prove combinatorial identities is known as the [Egorychev method](https://en.wikipedia.org/wiki/Egorychev_method), and it can make quick work of difficult identities involving finitie and infinite sums of binomial coefficients. For example, we can easily evaluate the sum

$$\sum_{k=0}^n\binom{n}{k}^2$$

as follows

$$\begin{align*}\sum_{k=0}^n\binom{n}{k}^2 &= \frac{1}{2\pi i}\oint_C\frac{(1+z)^n}{z}\sum_{k=0}^n\binom{n}k\frac{1}{z^k}\,\mathrm dz\\  &= \frac{1}{2\pi i}\oint_C\frac{(1+z)^n}{z}\left(1+\frac{1}{z} \right )^n\,\mathrm dz \\  &=\frac{1}{2\pi i}\oint_C\frac{(1+z)^{2n}}{z^{n+1}}\,\mathrm dz \\  &= \binom{2n}{n}.\end{align*}$$

Hence we have

$$\sum_{k=0}^n\binom{n}{k}^2=\binom{2n}{n}.$$

## Further examples

Lets prove that

$$\sum_{k=0}^n k\binom{n}{k}^2=n\binom{2n-1}{n}.$$

First note that by differentiating

$$(1+x)^n=\sum_{k=0}^n\binom{n}{k}x^k$$

we get

$$n(1+x)^{n-1}=\sum_{k=0}^nk\binom{n}{k}x^{k-1}.$$

Then multiplying each side by x yields

$$nx(1+x)^{n-1}=\sum_{k=0}^nk\binom{n}{k}x^k.$$

Now let $n\geq1$,

$$\begin{align*}\sum_{k=0}^nk\binom{n}{k}^2 &= \sum_{k=0}^n\frac{k}{2\pi i}\binom{n}{k}\oint_C\frac{(1+z)^n}{z^{k+1}}\,\mathrm dz \\&= \frac{1}{2\pi i}\oint_C\frac{(1+z)^n}{z}\sum_{k=0}^nk\binom{n}{k}\frac{1}{z^k}\,\mathrm dz \\&= \frac{1}{2\pi i}\oint_C\frac{(1+z)^n}{z}\cdot \frac{n}{z}\left(1+\frac{1}{z} \right )^{n-1}\,\mathrm dz \\&= \frac{n}{2\pi i}\oint_C\frac{(1+z)^{2n-1}}{z^{n+1}}\,\mathrm dz \\&= n\binom{2n-1}{n}.\end{align*}$$

### A Fibonacci identity

In order to show that

$$\sum_{k=0}^n\binom{n+k}{2k}=F_{2n+1}$$

we may make use of

$$\binom{n}{k}=0\;\text{if}\;k>n$$

and [Binet's formula](https://en.wikipedia.org/wiki/Fibonacci_sequence#Closed-form_expression). Let $\phi=(1+\sqrt{5})/2$ and $\bar{\phi}=(1-\sqrt{5})/2$, then

$$\begin{align*}\sum_{k=0}^n\binom{n+k}{2k} &=\sum_{k=0}^\infty\binom{n+k}{2k} \\  &=\sum_{k=0}^\infty\frac{1}{2\pi i}\oint_C\frac{(1+z)^{n+k}}{z^{2k+1}}\,\mathrm dz \\  &=\frac{1}{2\pi i}\oint_C\frac{(1+z)^n}{z}\sum_{k=0}^\infty\left(\frac{1+z}{z^2}\right)^k\,\mathrm dz \\  &=\frac{1}{2\pi i}\oint_C\frac{z(1+z)^n}{z^2-z-1}\,\mathrm dz, \\ &\qquad\text{where }C\text{ encircles the poles at }\phi\text{ and }\bar{\phi} \\ &=\frac{1}{2\pi i}\oint_C\frac{z(1+z)^n}{(z-\phi)(z-\bar{\phi})}\,\mathrm dz \\  &=\frac{\phi(1+\phi)^n}{\phi-\bar{\phi}}+\frac{\bar{\phi}(1+\bar{\phi})^n}{\bar{\phi}-\phi} \\  &=\frac{\phi(1+\phi)^n-\bar{\phi}(1+\bar{\phi})^n}{\sqrt{5}} \\  &=\frac{\phi\cdot\phi^{2n}-\bar{\phi}\cdot\bar{\phi}^{2n}}{\sqrt{5}} \\  &=F_{2n+1} \end{align*}$$

as was desired.

