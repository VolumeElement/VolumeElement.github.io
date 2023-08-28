---
title: A Tangent "Zeta Function"
# author: dxdydz
date: 2023-08-28 15:15:00 -0400
categories: [Calculus]
tags: [complex analysis, infinite series, infinite products, generating functions]
math: True
pin: False
---

Let the sequence $\left\\{x_n\right\\}_{n=1}^\infty$ be the positive solutions to $\tan(x)=x$ ordered by increasing magnitude and define the function

$$\zeta_t(s)=\sum_{n=1}^\infty\frac{1}{x_n^s}.$$

It is not hard to show that $\zeta_t(s)$ converges for $\Re s>1$. Also consider the function

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