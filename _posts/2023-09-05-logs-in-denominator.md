---
title: Some Integrals with Logarithms in the Denominator
# author: dxdydz
date: 2023-09-05 15:40:00 -0400
categories: [Calculus]
tags: [integration]
math: True
pin: False
---

## Problem

Evaluate

$$I=\int_0^1\frac{1-x}{1+x}\cdot\frac{1}{\ln(x)}\,\mathrm dx.$$

## Solution

Define the function

$$I(s)=\int_0^1\frac{1-x}{1+x}\cdot\frac{x^s}{\ln(x)}\,\mathrm dx$$

so that $I(0)=I$ and $\lim_{s\to\infty}I(s)=0$, then consider $I'(s)$. We have

$$\begin{align*}I'(s) &=\int_0^1\frac{1-x}{1+x}x^s\,\mathrm dx \\  &=\int_0^1\frac{(1-x)^2}{1-x^2}x^s\,\mathrm dx \\  &=\frac{1}{2}\int_0^1\frac{(1-u^{1/2})^2u^{s/2}}{(1-u^2)u^{1/2}}\,\mathrm du,\,x=u^{1/2} \\  &\;\;\vdots\qquad\text{(some unexciting algebra)} \\  &=\int_0^1\frac{1-u^{s/2}}{1-u}\,\mathrm du-\frac{1}{2}\int_0^1\frac{1-u^{(s+1)/2}}{1-u}\,\mathrm du-\frac{1}{2}\int_0^1\frac{1-u^{(s-1)/2}}{1-u}\,\mathrm du \\  &= \text{H}_{s/2}-\text{H}_{(s+1)/2}-\text{H}_{(s-1)/2} \\ &= \text{H}_{s/2}-\text{H}_{(s-1)/2}-\frac{1}{1+s} \\ &= \psi\left(\frac{s}{2}+1 \right )-\psi\left(\frac{s+1}{2} \right )-\frac{1}{1+s}\end{align*}$$

where $\text{H}_z$ is the zth harmonic number and $\psi(z)$ is the digamma function. Integrating and making use of the special values of $I(s)$ that we noted before yields the result we're after.

$$\begin{align*}I &= I(0) \\  &=-(\lim_{s\to\infty}I(s)-I(0)) \\  &=-\int_0^\infty I'(s)\,\mathrm ds \\  &=-2\left[\ln\left(\frac{\Gamma\left(\frac{s}{2}+1 \right )}{\sqrt{1+s}\Gamma\left(\frac{s+1}{2} \right )} \right ) \right ]\Bigg\vert_0^\infty \\  &=\ln\left(\frac{2}{\pi} \right ). \end{align*}$$

## Similar integrals

The above can be generalized to

$$\int_0^1\frac{1-x}{1+x+x^2+\cdots+x^n}\cdot\frac{1}{\ln(x)}\,\mathrm dx=\ln\left(\frac{\Gamma^2\left(\frac{s+2}{n+1}\right)}{\Gamma\left(\frac{s+1}{n+1}\right)\Gamma\left(\frac{s+3}{n+1}\right)}\right).$$

Another neat integral is

$$\int_0^1\frac{x^2-1}{1+x+x^2+x^3+x^4}\cdot\frac{1}{\ln(x)}\,\mathrm dx.$$

Can you find its value?

<details> 
  <summary>click to reveal answer </summary>
   ln(&phi;) where &phi; is the golden ratio
</details>
