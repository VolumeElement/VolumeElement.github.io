---
title: An Integral for the Euler-Mascheroni Constant
# author: dxdydz
date: 2023-07-12 16:00:00 -0400
categories: [Calculus]
tags: [integration, infinite series]
math: True
pin: False
---

## Problem

Evaluate

$$\int_0^1\left(\frac{1}{1-x}+\frac{1}{\ln(x)}\right)\mathrm dx.$$

## Solution

First we show that the integral

 $$\displaystyle{I=\int_0^\infty\left(\frac{1}{e^x-1}-\frac{e^{-x}}{x}\right)\,\mathrm dx}$$

converges. For positive $x$ we have $xe^x+1>e^x$, which implies

$$\displaystyle{\frac{1}{e^x-1}>\frac{e^{-x}}{x}.}$$

And the integrand is bounded above on $(0,\,\infty)$ as

$$\displaystyle{\frac{1}{e^x-1}-\frac{e^{-x}}{x}<\frac{1}{e^x-1}-\frac{e^{-x}}{e^x-1}=e^{-x}.}$$

So the integral converges and $0<I<1$.

Let $\Re(s)>1$ and define the function

$$\displaystyle{I(s)=\int_0^\infty\left(\frac{1}{e^x-1}-\frac{e^{-x}}{x}\right)x^{s-1}\,\mathrm dx.}$$

The integral representations of the gamma function and the Riemann zeta function quickly gives

$$\displaystyle{\begin{align*}I(s) &=\Gamma(s)\zeta(s)-\Gamma(s-1) \\ &=\Gamma(s)\left(\zeta(s)-\frac{1}{s-1}\right)\end{align*}}$$

which holds for at least $\Re(s)>1$.

Observing that $\Gamma(s)\left(\zeta(s)-\frac{1}{s-1}\right)$ has a removable singularity at $s=1$ and is the analytic continuation of $I(s)$, we may now evaluate $I$ using a one-sided limit and making use of the Laurent expansion of the zeta function about its pole:

$$\displaystyle{\begin{align*}I &=\lim_{x\to1^+}I(x) \\  &=\lim_{x\to1^+}\Gamma(x)\left(\zeta(x)-\frac{1}{x-1}\right) \\  &=\lim_{x\to1^+}\Gamma(x)\left(\frac{1}{x-1}+\gamma+o(x-1)-\frac{1}{x-1}\right) \\  &=\gamma \end{align*}}$$

where $\gamma$ is the Euler-Mascheroni constant.

Lastly,

$$\displaystyle{\begin{align*}I &=\int_0^\infty\left(\frac{1}{e^x-1}-\frac{e^{-x}}{x} \right )\,\mathrm dx \\  &=\int_0^1\left(\frac{1}{1-x}+\frac{1}{\ln(x)} \right )\,\mathrm dx,\qquad x\mapsto-\ln(x),\end{align*}}$$

so

$$\int_0^1\left(\frac{1}{1-x}+\frac{1}{\ln(x)}\right)\mathrm dx=\gamma.$$

## Another solution

The following elegant proof is by Horseshoe_Crab.

$$\begin{align*}\int_0^1\left(\frac{1}{1-x}+\frac{1}{\ln(x)}\right)\mathrm dx &=\int_0^1\left(\sum_{n=0}^\infty x^n-\int_0^\infty x^t\,\mathrm dt \right )\,\mathrm dx \\  &=\lim_{N\to\infty}\int_0^1\left(\sum_{n=0}^N x^n-\int_0^N x^t\,\mathrm dt \right )\,\mathrm dx, \\ &\qquad\text{we may interchange summation and integration as all terms are positive} \\  &=\lim_{N\to\infty}\left(\sum_{n=0}^N\int_0^1x^n\,\mathrm dx-\int_0^N\int_0^1x^t\mathrm dx\mathrm dt \right ) \\  &=\lim_{N\to\infty}\left(\sum_{n=0}^N\frac{1}{1+n}-\int_0^N\frac{1}{1+t}\,\mathrm dt \right ) \\  &= \lim_{N\to\infty}\left(H_N-\ln(N) \right ).\end{align*}$$

This last limit is the defintion for $\gamma$.