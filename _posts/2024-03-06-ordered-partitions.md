---
title: An Ordered Partition Problem
# author: dxdydz
date: 2024-03-06 10:20:00 -0400
categories: [Number Theory]
tags: [infinite series, generating functions, partitions]
math: True
pin: False
---

[A problem](https://youtu.be/iJ8pnCO0nTY?t=2943) given by Mathologer is the following: Pick any positive integer, say $n=4$, then write out all of its ordered partitions

$$\begin{align*}4 &=4 \\ 4 &=3+1 \\ 4 &=1+3 \\ 4 &=2+2 \\ 4 &=2+1+1 \\ 4 &=1+2+1 \\ 4 &=1+1+2 \\ 4 &=1+1+1+1.\end{align*}$$

Then change addition to multiplication,

$$\begin{align*}4 &=4 \\ 3 &=3\cdot1 \\ 3 &=1\cdot3 \\ 4 &=2\cdot2 \\ 2 &=2\cdot1\cdot1 \\ 2 &=1\cdot2\cdot1 \\ 2 &=1\cdot1\cdot2 \\ 1 &=1\cdot1\cdot1\cdot1\end{align*}$$

and add everything up to get

$$4+3+3+4+2+2+2+1=21.$$

We will call the number reached by this process $S_n$, so $S_4=21.$ The question posed is: Can we find an easier rule that tells us what number we'll get at the end of this process?

# Solution

First we will hunt for a closed form of the generating function

$$h(x)=\sum_{n=1}^\infty S_nx^n.$$

Note that

$$\left(\sum_{n=1}^\infty nx^n\right)^k$$

is the generating function for the sum of all the ordered products containing $k$ factors we get when starting from $n$. (I.e., the $k\text{th}$ power of this sum associates a number in an exponent of $x$ to its sums of products of $k$ numbers as the coefficient of $x$.) If we sum over all $k$, by the definition of $S_n$, we get $h(x)$,

$$\begin{align*}h(x) &=\sum_{k=1}^\infty\left(\sum_{n=1}^\infty nx^n\right)^k \\  &=\sum_{k=1}^\infty\left(\frac{x}{(1-x)^2}\right)^k \\  &=\frac{x}{1-3x+x^2}.\end{align*}$$

Observing that the first few $S_n$ values come from a familiar sequence inspires the following leap:

$$h(x)=\frac{f(x^{1/2})+f(-x^{1/2})}{2}$$

where

$$\begin{align*}f(x) &=\sum_{n=0}^\infty F_nx^n \\  &=\frac{x}{1-x-x^2} \end{align*}$$

is the generating function for the Fibonacci numbers with $F_0=0$ and $F_1=1$. The representation of $h(x)$ in terms of $f(x)$ tells us that

$$h(x)=\sum_{n=1}^\infty F_{2n}x^n.$$

Equating like coefficients with the series in the original defintion of $h(x)$ yields

$$S_n=F_{2n}.$$