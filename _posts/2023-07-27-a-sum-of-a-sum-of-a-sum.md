---
title: A Sum of a Sum of a Sum
# author: dxdydz
date: 2023-07-27 16:40:00 -0400
categories: [Calculus]
tags: [infinite series, integration]
math: True
pin: False
---

## Problem

Evaluate the sum

$$S=\sum_{n=1}^\infty\frac{1}{n^3}\sum_{k=1}^nH_k$$

where $H_k=\sum_{m=1}^k 1/m$ is the kth harmonic number.

# Solution

Using the same method as in the solution of [AMM12194](/2023-06-18-AMM12194) we have

$$\sum_{k=1}^nH_k=(n+1)H_n-n$$

and it follows that

$$\begin{align*}S &=\sum_{n=1}^\infty\frac{H_n}{n^2}+\sum_{n=1}^\infty\frac{H_n}{n^3}-\sum_{n=1}^\infty\frac{1}{n^2} \\  &=\sum_{n=1}^\infty\frac{H_n}{n^2}+\sum_{n=1}^\infty\frac{H_n}{n^3}-\frac{\pi^2}{6}.\end{align*}$$

The first Euler sum may be evaluated using the integral formula for the nth harmonic number

$$H_n=\int_0^1\frac{1-x^n}{1-x}\,\mathrm dx$$

and the dilogarithm,

$$\displaystyle{\begin{align*}\sum_{n=1}^\infty\frac{H_n}{n^2} &=\int_0^1\frac{\zeta(2)-\text{Li}_2(x)}{1-x}\,\mathrm dx,\text{ switch }\int\text{ and }\sum\text{ (as all terms have the same sign)} \\ &=\left[-\left(\zeta(2)-\text{Li}_2(x) \right )\ln(1-x) \right ]|_0^1+\int_0^1\frac{\ln^2(1-x)}{x}\,\mathrm dx,\text{ by parts with }\,u=\zeta(2)-\text{Li}_2(x),\,\mathrm dv=\frac{\ln(1-x)}{x}\,\mathrm dx \\ &=\int_0^1\frac{\ln^2(1-x)}{x}\,\mathrm dx \\ &=\int_0^\infty\frac{u^2}{e^u-1}\,\mathrm du,\,1-x=e^{-u} \\ &=2\zeta(3),\end{align*}}$$

where in the last line we've used the classic representation of the Riemann zeta function as a Mellin transform. Orignainally, when I created this problem, I used the same method to evaluate the second Euler sum, but instead I will present an evaluation by chompchump who was able to evaluate this second sum but not the first. Interestingly, this method does not work on the first sum.

We begin by noting that

$$H_n=\sum_{k=1}^\infty\left(\frac{1}{k}-\frac{1}{k+n}\right)$$

so that

$$\begin{align*}\sum_{n=1}^\infty\frac{H_n}{n^3} &= \sum_{n=1}^\infty\frac{1}{n^3}\sum_{k=1}^\infty\left(\frac{1}{k}-\frac{1}{k+n}\right)\\  &=\sum_{n=1}^\infty\sum_{k=1}^\infty\frac{1}{n^2k(k+n)} \\  &= \sum_{n=1}^\infty\sum_{k=1}^\infty\frac{1}{k^2n(n+k)}.\end{align*}$$

Now examine twice the sum,

$$\begin{align*}2\sum_{n=1}^\infty\frac{H_n}{n^3} &= \\  &=\sum_{n=1}^\infty\sum_{k=1}^\infty\frac{1}{n^2k(k+n)}+\sum_{n=1}^\infty\sum_{k=1}^\infty\frac{1}{k^2n(n+k)} \\  &=\sum_{n=1}^\infty\sum_{k=1}^\infty\left(\frac{1}{n^2k(k+n)}+\frac{1}{k^2n(n+k)} \right ) \\  &=\sum_{n=1}^\infty\sum_{k=1}^\infty\frac{1}{n^2k^2} \\ &= \zeta^2(2) \\ &= \frac{\pi^4}{36}.\end{align*}$$

This implies that

$$\sum_{n=1}^\infty\frac{H_n}{n^3}=\frac{\pi^4}{72}.$$

Putting it all together yields

$$S=2\zeta(3)+\frac{\pi^4}{72}-\frac{\pi^2}{6}.$$