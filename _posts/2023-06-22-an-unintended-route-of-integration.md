---
title: An Unintended Route of Integration
# author: dxdydz
date: 2023-06-22 17:10:00 -0400
categories: [Caclulus]
tags: [infinite series, integration]
math: True
pin: False
---

The integral

$$\int_0^\infty\frac{\ln(x)}{(1+x)(1+x^2)}\,\mathrm dx$$

was brought to me by a friend, who came about it in a context that suggested for it to be done by contour integration. Surpsisingly, there is a cute trick that allows the integral to be evaluated using the Dirichlet eta function, which is related to the Riemann zeta function through the formula $\eta(s)=(1-2^{1-s})\zeta(s)$,

$$\begin{align*}    \int_0^\infty\frac{\ln(x)}{(1+x)(1+x^2)}\,\mathrm dx &= \int_{-\infty}^\infty\frac{u e^u}{(1+e^u)(1+e^{2u})}\,\mathrm du,\qquad x=e^u \\    &= \int_0^\infty\frac{u e^u}{(1+e^u)(1+e^{2u})}\,\mathrm du-\int_0^{-\infty}\frac{u e^u}{(1+e^u)(1+e^{2u})}\,\mathrm du \\    &= \int_0^\infty\underset{\times e^{-3u}/e^{-3u}}{\underbrace{\frac{u e^{-2u}}{(1+e^{-u})(1+e^{-2u})}}}\,\mathrm du-\int_0^\infty\underset{u\mapsto -u}{\underbrace{\frac{u e^{-u}}{(1+e^{-u})(1+e^{-2u})}}}\,\mathrm du \\    &= \int_0^\infty\left(\frac{u}{1+e^{-u}}-\frac{u}{1+e^{-2u}}\right)\,\mathrm du,\;\text{combine / partial fractions} \\    &= \int_0^\infty u\left(\sum_{n=0}^\infty (-1)^n e^{-nu}-\sum_{n=0}^\infty (-1)^n e^{-2nu}\right)\,\mathrm du \\    &= \int_0^\infty u\left(\sum_{n=1}^\infty (-1)^n e^{-nu}-\sum_{n=1}^\infty (-1)^n e^{-2nu}\right)\,\mathrm du \\    &= \sum_{n=1}^\infty(-1)^n\int_0^\infty u e^{-nu}\,\mathrm du-\sum_{n=1}^\infty(-1)^n\int_0^\infty u e^{-2nu}\,\mathrm du, \\    &\qquad\text{split and use dominated convergence on }(\epsilon,\,\infty) \\    &= \sum_{n=1}^\infty\frac{(-1)^n}{n^2}-\frac{1}{2}\sum_{n=1}^\infty\frac{(-1)^n}{n^2} \\    &= -\frac{1}{2}\eta(2) \\    &= -\frac{\pi^2}{24}.\end{align*}$$