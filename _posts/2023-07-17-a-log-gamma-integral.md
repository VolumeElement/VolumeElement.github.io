---
title: A log-gamma Integral
# author: dxdydz
date: 2023-07-17 10:40:00 -0400
categories: [Calculus]
tags: [integration, infinite series, infinite products]
math: True
pin: False
---

## Problem

Evaluate

$$I=\int_0^1\ln(\Gamma(x))\,\mathrm dx.$$

## Solution

Let $x\mapsto1-x$ so

$$I=\int_0^1\ln(\Gamma(1-x))\,\mathrm dx.$$

If we take the average of these two integrals and apply the reflection formula, $\Gamma(x)\Gamma(1-x)=\pi/\sin(\pi x)$, we see that

$$\begin{align*}I &=\frac{1}{2}\int_0^1\ln(\Gamma(x)\Gamma(1-x))\,\mathrm dx \\  &=\frac{1}{2}\int_0^1\ln\left(\frac{\pi}{\sin(\pi x)} \right )\,\mathrm dx \\  &=\frac{1}{2}\ln(\pi)-\frac{1}{2}\underset{J}{\underbrace{\int_0^1\ln(\sin(\pi x))\,\mathrm dx}} \\  &=\frac{1}{2}\ln(\pi)-\frac{1}{2}\int_0^1\ln\left(2\sin\left(\frac{\pi x}{2}\right)\cos\left(\frac{\pi x}{2}\right) \right )\,\mathrm dx \\  &=\frac{1}{2}\ln(\pi)-\frac{1}{2}\ln(2)-\int_0^{1/2}\ln(\sin(\pi x)\cos(\pi x))\,\mathrm dx,\qquad x\mapsto 2x \\  &= \frac{1}{2}\ln(\pi)-\frac{1}{2}\ln(2)-\int_0^{1/2}\ln(\sin(\pi x))\,\mathrm dx-\int_0^{1/2}\ln(\cos(\pi x))\,\mathrm dx \\  &= \frac{1}{2}\ln(\pi)-\frac{1}{2}\ln(2)-\frac{1}{2}J-\frac{1}{2}J \\ &= \frac{1}{2}\ln(\pi)-\frac{1}{2}\ln(2)-J.\end{align*}$$

We can solve

$$\frac{1}{2}\ln(\pi)-\frac{1}{2}J=\frac{1}{2}\ln(\pi)-\frac{1}{2}\ln(2)-J$$

to get

$$\int_0^1\ln(\sin(\pi x))\,\mathrm dx=-\ln(2),$$

which tells us

$$\int_0^1\ln(\Gamma(x))\,\mathrm dx=\frac{1}{2}\ln(2\pi).$$

## Some bonus series

Taking the logarithm of the product

$$\frac{\sin(\pi x)}{\pi x}=\pi x\prod_{n=1}^\infty\left(1-\frac{x^2}{n^2}\right)$$

yields the infinite series

$$\ln(\sin(\pi x))=-\ln(\pi)-\ln(x)-\sum_{n=1}^\infty\frac{\zeta(2n)}{n}x^{2n},\qquad |x|<1.$$

Integrating this from $0$ to $1$ shows

$$\sum_{n=1}^\infty\frac{\zeta(2n)}{n(2n+1)}=\ln(2\pi)-1.$$

Similarly, if we integrate [the series for the log-gamma function](https://proofwiki.org/wiki/Taylor_Series_of_Logarithm_of_Gamma_Function),

$$\ln(\Gamma(x+1))=-\gamma x+\sum_{n=2}^\infty\frac{(-1)^n\zeta(n)}{n}x^n,$$

results in the identity

$$\sum_{n=2}^\infty\frac{(-1)^n\zeta(n)}{n(n+1)}=\frac{1}{2}\ln(2)+\frac{1}{2}\ln(\pi)+\frac{\gamma}{2}-1.$$