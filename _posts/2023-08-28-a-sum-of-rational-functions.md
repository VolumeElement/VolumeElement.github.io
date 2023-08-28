---
title: A Sum of Rational Functions
# author: dxdydz
date: 2023-08-26 13:50:00 -0400
categories: [Calculus]
tags: [infinite series, infinite products]
math: True
pin: False
---

## Problem

Find the value of

$$f(x)=\sum_{n=0}^\infty\frac{2^n x^{2^n-1}-2^{n+1}x^{2^{n+1}-1}}{1-x^{2^n}+x^{2^n}}$$

when $x=1/2$.

## Solution

The big hint in this problem is that the summand is the logarithmic derivative of $1/(1-x^{2^n}+x^{2^{n+1}})$, hence

$$f(x)=-\frac{\mathrm d}{\mathrm dx}\ln\prod_{n=0}^\infty(1-x^{2^n}+x^{2^{n+1}})$$

and we should investigate the above infinite product. Using induction we may show that

$$\prod_{n=0}^m(1-x^{2^n}+x^{2^{n+1}})=\frac{1+x^{2^{m+1}}+x^{2^{m+2}}}{1+x+x^2}.\tag{1}$$

**Base case:**

When $m=0$ we have

$$\prod_{n=0}^m(1-x^{2^n}+x^{2^{n+1}})=1-x+x^2$$

on the left hand side of $(1)$. Setting $m=0$ on the right hand side yields

$$\frac{1+x^2+x^4}{1+x+x^2}=1-x+x^2,$$

so the $m=0$ case holds true.

**Induction step:**

We want to show that the truth of the $m\text{th}$ case of $(1)$ implies the truth of the $(m+1)\text{th}$ case of $(1)$. So assume $(1)$ is true in the $m\text{th}$ case, then we have

$$\begin{align*}\prod_{n=0}^{m+1}(1-x^{2^n}+x^{2^{n+1}}) &=\left( \prod_{n=0}^{m}(1-x^{2^n}+x^{2^{n+1}})\right )(1-x^{2^{m+1}}+x^{2^{m+2}}) \\  &=\frac{1+x^{2^{m+1}}+x^{2^{m+2}}}{1+x+x^2}(1-x^{2^{m+1}}+x^{2^{m+2}}) ,\qquad\text{by our assumption} \\ &= \frac{1+x^{2^{m+2}}+x^{2^{m+3}}}{1+x+x^2},\end{align*}$$

which demonstrates the truth of the $(m+1)\text{th}$ case. Now we may take $|x|<1$ so

$$\lim_{m\to\infty}\prod_{n=0}^m(1-x^{2^n}+x^{2^{n+1}}) =\frac{1}{1+x+x^2},$$

which tells us

$$\begin{align*}f(x) &=\frac{\mathrm d}{\mathrm dx}\ln(1+x+x^2) \\  &= \frac{1+2x}{1+x+x^2}.\end{align*}$$

Finally, we may conclude that $f(1/2)=8/7.$