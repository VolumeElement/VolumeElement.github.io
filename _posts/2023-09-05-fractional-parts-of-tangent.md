---
title: An Integral Involving Fractional Parts of the Tangent
# author: dxdydz
date: 2023-09-05 17:20:00 -0400
categories: [Calculus]
tags: [integration, infinite series]
math: True
pin: False
---

## Problem

Evaluate

$$I=\int_0^\frac{\pi}{2}\frac{\left\{\tan(x)\right\}}{\tan(x)}\,\mathrm dx$$

where $\left\\{x\right\\}$ denotes the fractional part of $x$.

## Solution

First let $x=\text{arctan}(u)$ so that

$$I=\int_0^\infty\frac{\left\{u\right\}}{u(1+u^2)}\,\mathrm du$$

then expand the integral into an infinite series as follows,

$$\begin{align*}I &=\int_0^\infty\frac{u-\left \lfloor u \right \rfloor}{u(1+u^2)}\,\mathrm du \\ &=\sum_{n=0}^\infty\int_n^{n+1}\frac{u-\left \lfloor u \right \rfloor}{u(1+u^2)}\,\mathrm du \\  &=\sum_{n=0}^\infty\int_0^1\frac{u+n-\left \lfloor u+n \right \rfloor}{(u+n)(1+(u+n)^2)}\,\mathrm du,\,u\mapsto u+n \\  &=\int_0^1 u\sum_{n=0}^\infty\frac{1}{(u+n)(1+(u+n)^2)}\,\mathrm du \\  &= \int_0^1 u\sum_{n=1}^\infty\left( \frac{1}{n-1+u}-\frac{1}{2(n-1+u+i)}-\frac{1}{2(n-1+u-i)}\right )\,\mathrm du \\ &= \int_0^1 u\left(\frac{1}{2}\psi(u+i)+\frac{1}{2}\psi(u-i)-\psi(u)\right)\,\mathrm du\tag{1}\end{align*}$$

where in the last line we've used the series

$$\psi(1+z)=-\gamma+\sum_{n=1}^\infty\left(\frac{1}{n}-\frac{1}{n+z}\right)$$

for the digamma function. The integrals in $(1)$ are readily done by parts to get

$$\begin{align*}\int_0^1 u\psi(u)\,\mathrm du &=\int_0^1\ln(\Gamma(u))\,\mathrm du \\  &= \frac{1}{2}\ln(2\pi),\tag{2}\end{align*}$$

 the detail for this is shown [here](https://volumeelement.github.io/posts/a-log-gamma-integral/). For the remaining two integrals we have

 $$\begin{align*}\int_0^1\ln(\Gamma(u+\alpha))\,\mathrm du &=\int_\alpha^{\alpha+1}\ln(\Gamma(u))\,\mathrm du \\  &=\int_0^1\ln(\Gamma(u))\,\mathrm du+\int_1^{\alpha+1}\ln(\Gamma(u))\,\mathrm du-\int_0^\alpha\ln(\Gamma(u))\,\mathrm du \\  &=\frac{1}{2}\ln(2\pi)+\int_0^\alpha\ln(\Gamma(u+1))\,\mathrm du-\int_0^\alpha\ln(\Gamma(u))\,\mathrm du \\  &=\frac{1}{2}\ln(2\pi)+\int_0^\alpha\ln\left(\frac{\Gamma(u+1)}{\Gamma(u)}\right)\,\mathrm du \\  &= \frac{1}{2}\ln(2\pi)+\int_0^\alpha\ln(u)\,\mathrm du \\ &= \frac{1}{2}\ln(2\pi)+\alpha\ln(\alpha)-\alpha.\tag{3}\end{align*}$$

Using $(2)$ and $(3)$ on $(1)$ tells us that

$$I=\frac{1}{2}\ln(\Gamma(1+i)\Gamma(1-i))+\frac{\pi}{2}.$$

Recognizing that the product of gamma fucntions may be written as $i\Gamma(i)\Gamma(1-i)$ and applying the reflection formula gives the much nicer closed form

$$\int_0^\frac{\pi}{2}\frac{\left\{\tan(x)\right\}}{\tan(x)}\,\mathrm dx=\frac{1}{2}\ln(\pi\text{csch}(\pi))+\frac{\pi}{2}.$$