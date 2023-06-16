---
title: A Product of Derivatives
# author: dxdydz
date: 2023-06-16 10:00:00 -0400
categories: [Calculus]
tags: [differential equations]
math: True
pin: False
---

## Problem

Find all $n\in\mathbb{N}$ such that

$$f(x)=\prod_{k=1}^nf^{(k)}(x)$$

has a real solution of the form $f(x)=ax^r$ with $a\neq0$.

## Solution

We show that such an $f$ exists iff $n\neq1$ or $n\not\equiv5,\,7\,(\text{mod}\,8).$

We start by plugging the solution type of interest into the differential equation to get

$$\begin{align*}    ax^r &= a^nrx^{r-1}\cdot r(r-1)x^{r-2}\cdots\left(r(r-1)\cdots(r-n+1)x^{r-n}\right) \\    &= a^n\prod_{k=0}^{n-1}(r-k)^{n-k}x^{nr-\frac{n(n+1)}{2}}.\end{align*}$$

Solving for $r$ and $a$ shows that

$$r_n=\frac{n(n+1)}{2(n-1)}$$

and

$$a_n=\left(\displaystyle\prod_{k=0}^{n-1}\left(\frac{n(n+1)}{2(n-1)}-k\right)^{k-n}\right)^{\frac{1}{n-1}}.$$

Clearly, these are not defined for $n=1$, so that case is done. Now for solutions to not exist for other $n$ we must have two things happen simultaneously:

1. The $(n-1)$th root that occurs in $a_n$ must be even.
2. The number of negative factors in $\prod_{k=0}^{n-1}\left(\frac{n(n+1)}{2(n-1)}-k\right)^{k-n}$ must be odd.

The first condition implies that $n=2m+1$, combined with the second condition we have

$$\begin{align*}    \text{sgn}\prod_{k=0}^{n-1}\left(\frac{n(n+1)}{2(n-1)}-k\right)^{k-n} &=\text{sgn}\prod_{k=0}^{2m}\left(\frac{n(n+1)}{2(n-1)}-k\right)^{k-2m-1} \\    &= \text{sgn}\prod_{k=0}^{2m}\left(\frac{n(n+1)}{2(n-1)}-k\right)^{k-1} \\    &= \text{sgn}\prod_{k=0}^{m}\left(\frac{n(n+1)}{2(n-1)}-2k\right)^{2k-1} \\    &= \text{sgn}\prod_{k=0}^{m}\left(\frac{n(n+1)}{2(n-1)}-2k\right)\end{align*}$$

as negative factors are only contributed when $k$ is even. For a factor to be negative we must also have

$$\begin{align*}    k &> \frac{n(n+1)}{4(n-1)} \\    &= \frac{(2m+1)(m+1)}{4m} \\    &= \frac{m}{2}+\frac{3}{4}+\frac{1}{4m}.\end{align*}$$

So we must find when the number of $k$ satisfying

$$\left\lceil \frac{m}{2}+\frac{3}{4}+\frac{1}{4m} \right\rceil\leq k \leq m$$
is odd because
$$\text{sgn}\prod_{k=0}^{m}\left(\frac{n(n+1)}{2(n-1)}-2k\right)=\prod_{k=\left\lceil \frac{m}{2}+\frac{3}{4}+\frac{1}{4m} \right\rceil}^m(-1).$$
Or put differently, when is
$$g(m)=m-\left\lceil \frac{m}{2}+\frac{3}{4}+\frac{1}{4m} \right\rceil$$
odd? Note that the ceiling function only increases every other value of $m$ and $g(m)$ is odd when $m=2$ and $m=3$, so $g(m)$ alternates odd/even like

| $m$ | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | $\cdots$ |
| $g(m)$ | o | o | e | e | o | o | e | e | o | $\cdots$ |

(Alternatively, investigate the cases $m=4j$, $m=4j+1$, $m=4j+2$, and $m=4j+3$.) These values of $m$ that make $g(m)$  odd are exactly those satisfying $m\equiv2,\,3\,(\text{mod }4).$ But $n=2m+1$ so this implies we must not have $n\equiv5,\,7\,(\text{mod}\,8)$. And we're done!