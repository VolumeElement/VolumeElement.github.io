---
title: An arctangent Integral
# author: dxdydz
date: 2024-09-08 8:40:00 -0400
categories: [Calculus]
tags: [integration]
math: True
pin: False
---

## Problem

Evaluate

$$-\int_1^\infty\frac{\mathrm dx}{x+x^2\arctan(x)+x^3+x^4\arctan(x)}.$$

## Solution

After factoring the integrand, we may evaluate the integral using a pair of substitutions,

$$\begin{align*}-\int_1^\infty\frac{\mathrm dx}{x(1+x^2)(1+x\arctan(x))}&=-\int_{\pi/4}^{\pi/2}\frac{\mathrm d\theta}{\tan(\theta)(1+\theta\tan(\theta))},\qquad x=\tan(\theta)\\&=-\int_{\pi/4}^{\pi/2}\frac{\cot^2(\theta)}{\theta+\cot(\theta)}\,\mathrm d\theta\\&=\int_{1+\pi/4}^{\pi/2}\frac{\mathrm du}{u},\qquad u=\theta+\cot(\theta)\\&=\ln\left(\frac{2\pi}{4+\pi}\right).\end{align*}$$