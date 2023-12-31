---
title: A Transcendence Proof
# author: dxdydz
date: 2023-07-08 9:20:00 -0400
categories: [Number Theory]
tags: [transcendental numbers]
math: True
pin: False
---

In general, proving the transcendence of a number is incredibly difficult, but there are some values that are amenable to rather quick transcendence proofs. Here we will show that

$$\alpha=\frac{\ln\left(1+\sqrt{3}\right)}{\ln\left(1+\sqrt{2}\right)}$$

is a transcendental number by use of a remarkable theorem called the Gelfond-Schneider theorem, which states that if  $a\in\bar{\mathbb{Q}}\setminus\left\\{0,\,1\right\\}$ and $b\in\bar{\mathbb{Q}}\setminus\mathbb{Q}$ then $a^b$ is transcendental.

## Proving $\alpha$ is transcendental

We start by assuming that $\alpha$ is rational, $\alpha=n/m$ for some integers $n$ and $m$ with $m\neq0$. This leads to

$$n\ln\left(1+\sqrt{2}\right)=m\ln\left(1+\sqrt{3}\right)$$

or

$$\left(1+\sqrt{2}\right)^n=\left(1+\sqrt{3}\right)^m.$$

Multiplying everything out, we can see that the above equation may be written as $a+b\sqrt{2}=c+d\sqrt{3}$, for some integers $a,\,b,\,c,\,d$. This implies that $d\sqrt{3}-b\sqrt{2}\in\mathbb{Z}.$ Since $d\sqrt{3}-b\sqrt{2}$ is an integer, its square

$$\left(d\sqrt{3}-b\sqrt{2}\right)^2=3d^2+2b^2-2db\sqrt{6}$$

is also an integer. But rearranging this would show that $\sqrt{6}$ is rational, a contradiction, therefore $\alpha$ is irrational. Now we may apply the Gelfond-Schneider theorem to show transcendence.

Suppose that $\alpha\in\bar{\mathbb{Q}}\setminus\mathbb{Q}$, then $\left(1+\sqrt{2}\right)^\alpha$ would be transcendental by the Gelfond-Schneider theorem. But

$$\begin{align*}\left(1+\sqrt{2}\right)^\alpha &= \left(1+\sqrt{2}\right)^{\log_{1+\sqrt{2}}\left(1+\sqrt{3} \right )}\\  &=1+\sqrt{3} \in\bar{\mathbb{Q}},\end{align*}$$

which is a contradiction, so $\alpha$ is transcendental.