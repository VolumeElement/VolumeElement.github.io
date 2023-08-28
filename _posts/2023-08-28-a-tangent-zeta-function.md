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