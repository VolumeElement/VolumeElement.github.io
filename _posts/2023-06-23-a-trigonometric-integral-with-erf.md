---
title: A Trigonometric Integral with Erf
# author: dxdydz
date: 2023-06-23 15:10:00 -0400
categories: [Caclulus]
tags: [differential equations, integration]
math: True
pin: False
---

## Problem

Evaluate

$$I=\int_0^{\pi/2}e^{-\sec^2(x)}\,\mathrm dx.$$

## Solution

Generalize the integral to

$$I=\int_0^{\pi/2}e^{-\alpha\sec^2(x)}\,\mathrm dx.$$

Using the substitution $x=\text{arcsec}(\sqrt{u+1}$ we get

$$\int_0^{\pi/2}e^{-\alpha\sec^2(x)}\,\mathrm dx = \frac{1}{2e^\alpha}\int_0^\infty\frac{e^{-\alpha u}}{(u+1)\sqrt{u}}\,\mathrm du.$$

We see that $I(1)=I,\,\lim_{\alpha\to\infty}I(\alpha)=0,$ and

$$\begin{align*}I(\alpha) &= \frac{1}{2e^\alpha}\int_0^\infty\frac{e^{-\alpha u}}{\sqrt{u}}\,\mathrm du-\frac{1}{2e^\alpha}\int_0^\infty\frac{\sqrt{u}}{u+1}e^{-\alpha u}\,\mathrm du\\ &= \frac{1}{2e^\alpha}\sqrt{\frac{\pi}{\alpha}}+\frac{1}{e^\alpha}\frac{\mathrm d}{\mathrm d\alpha}e^{\alpha}I(\alpha).\end{align*}$$

Rearrange the above to get

$$f(\alpha)-f'(\alpha)=\frac{1}{2}\sqrt{\frac{\pi}{\alpha}},$$

where $f(\alpha)=e^\alpha I(\alpha)$. Now multiply both sides by the integrating factor $\mu(\alpha)=e^{-\alpha},$ then reverse the product rule to show

$$\frac{\mathrm d}{\mathrm d\alpha}e^{-\alpha}f(\alpha)=-\frac{e^{-\alpha}}{2}\sqrt{\frac{\pi}{\alpha}}.$$

Integrating on the interval $ (with $x$ positive) yields

$$I(x)=\frac{\sqrt{\pi}}{2}\int_x^\infty\frac{e^{-\alpha}}{\sqrt{\alpha}}\,\mathrm d\alpha.$$

With some simple u-substitution we can show this is

$$I(x)=\frac{\pi}{2}(1-\text{erf}(\sqrt{x}))$$

where we've used the [error function](https://mathworld.wolfram.com/Erf.html). This implies

$$\int_0^{\pi/2}e^{-\sec^2(x)}\,\mathrm dx=\frac{\pi}{2}(1-\text{erf}(1)).$$

In general

$$\int_0^{\pi/2}e^{-\alpha\sec^2(x)}\,\mathrm dx=\frac{\pi}{2}(1-\text{erf}(\sqrt{\alpha})),\qquad \alpha\geq0.$$