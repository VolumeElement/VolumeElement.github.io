---
title: The Harmonic Series and Primes
# author: dxdydz
date: 2023-07-12 10:30:00 -0400
categories: [Number Theory]
tags: [infinite series, infinite products]
math: True
pin: False
---

The $n\text{th}$ harmonic number is given by

$$H_n=\sum_{k=1}^n\frac{1}{k}$$

and it is a well known fact that $H_n\to\infty$ as $n\to\infty$. Often this is proven by comparing the sum to the integral $\int_1^\infty\frac{1}{x}\,\mathrm dx$ or [this crafty proof](https://proofwiki.org/wiki/Harmonic_Series_is_Divergent#Proof_1), but there is another lesser known proof that I think is just as fun.

## Divergence of the harmonic series

We start with the inequality $e^x\geq1+x$, with equality only when $x=0$. If we apply this to the exponential of $H_n$ we get

$$\begin{align*}e^{H_n} &>\prod_{k=1}^n\left(1+\frac{1}{k} \right ) \\  &=\prod_{k=1}^n\frac{k+1}{k} \\  &=1+n.\end{align*}$$

Taking the natural logarithm of both sides tells us that $H_n>\ln(n+1)$, and $\ln(n+1)\to\infty$ as $n\to\infty$ yields the desired result.

## The infinitude of prime numbers

From the Euler product for the Riemann zeta function we have,

$$\sum_{n=1}^\infty\frac{1}{n}=\prod_p\frac{p}{p-1}.$$

Now if there were a finite number of prime numbers, the right hand side of the above equality would clearly be convergent, but this implies $H_n$ wouldn't tend to infinity. This is a contradiction, so there must be infinitely many prime numbers.