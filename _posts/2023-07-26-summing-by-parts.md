---
title: Summing by Parts
# author: dxdydz
date: 2023-07-26 18:25:00 -0400
categories: [Calculus]
tags: [infinite series]
math: True
pin: False
---

# Problem

Evaluate

$$S=\sum_{n=1}^\infty\frac{1}{n^2}\sum_{k=1}^n\frac{1}{k^2}.$$

# Solution

The formula for [summation by parts](https://en.wikipedia.org/wiki/Summation_by_parts) tells us that if we define

$$B_n=\sum_{k=0}^n b_k$$

so that for every $n>0$, $b_n=B_n-B_{n-1}$ we have

$$\sum_{n=0}^N a_nb_n=a_Nb_N-\sum_{n=0}^{N-1}B_n(a_{n+1}-a_n).$$

In order to evaluate $S$, consider the partial sum

$$S_N=\sum_{n=1}^N\frac{1}{n^2}\sum_{k=1}^n\frac{1}{k^2}$$

and let $b_n=1/n^2$ and $a_n=\sum_{k=1}^n 1/k^2.$ Applying summation by parts, we acquire an alternate formula for $S_N$,

$$\begin{align*}S_N &=\left(\sum_{k=1}^N\frac{1}{k^2} \right )^2-\sum_{n=1}^{N-1}\frac{1}{(n+1)^2}\sum_{k=1}^n\frac{1}{k^2} \\  &=\left(\sum_{k=1}^N\frac{1}{k^2} \right )^2-\sum_{n=1}^{N-1}\frac{1}{(n+1)^2}\left( -\frac{1}{(n+1)^2}+\sum_{k=1}^{n+1}\frac{1}{k^2}\right ) \\ &= \left(\sum_{k=1}^N\frac{1}{k^2} \right )^2-\sum_{n=1}^{N-1}\frac{1}{(n+1)^2}\sum_{k=1}^{n+1}\frac{1}{k^2}+\sum_{n=1}^{N-1}\frac{1}{(n+1)^4}.\end{align*}$$

In the limit as $N\to\infty$ this becomes

$$S=\zeta^2(2)-(S-1)+(\zeta(4)-1)$$

so $S=7\pi^4/360.$ In general one can show that

$$\sum_{n=1}^\infty\frac{1}{n^m}\sum_{k=1}^n\frac{1}{k^m}=\frac{1}{2}\zeta^2(m)+\frac{1}{2}\zeta(2m).$$