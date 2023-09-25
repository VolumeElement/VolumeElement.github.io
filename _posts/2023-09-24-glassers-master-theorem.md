---
title: Glasser's Master Theorem
# author: dxdydz
date: 2023-09-24 10:50:00 -0400
categories: [Calculus]
tags: [integration]
math: True
pin: False
---

 A quick way to make work of some challenging integrals is the following:

> **Glasser's Master Theorem:** Let $f(x)$ be a Riemann integrable function over $(-\infty,\,\infty)$ then
>
> $$\displaystyle{\int_{-\infty}^\infty f(x)\,\mathrm dx=\int_{-\infty}^\infty f\left(x-\frac{1}{x}\right)\,\mathrm dx.}$$
>
> $$\,$$

The proof is rather short and can be seen in [Glasser's original paper](https://www.ams.org/journals/mcom/1983-40-162/S0025-5718-1983-0689471-1/S0025-5718-1983-0689471-1.pdf).

## Example

Suppose we wish to evaluate

$$J=\int_0^\infty\sin^3\left(x^2+\frac{1}{x^2}\right)\,\mathrm dx.$$

We can start by seeing

$$\begin{align*}J &= \frac{1}{2}\int_{-\infty}^\infty\sin^3\left(x^2+\frac{1}{x^2}\right)\,\mathrm dx \\ &=\frac{1}{2}\int_{-\infty}^\infty\sin^3\left(\left(x-\frac{1}{x}\right)^2+2\right)\,\mathrm dx.  \end{align*}$$

Upon applying Glasser's Master theorem we have

$$\begin{align*}\int_0^\infty\sin^3\left(x^2+\frac{1}{x^2}\right)\,\mathrm dx &=\frac{1}{2}\int_{-\infty}^\infty\sin^3(x^2+2)\,\mathrm dx\\ &=\int_0^\infty\sin^3(x^2+2)\,\mathrm dx \\ &= \frac{1}{4}\int_0^\infty\left(3\sin(x^2+2)-\sin(3x^2+6) \right )\,\mathrm dx \\ 
 &=\frac{1}{4}\int_0^\infty\left(3\cos(2)\sin(x^2)+3\sin(2)\cos(x^2)-\cos(6)\sin(3x^2)-\sin(6)\cos(3x^2)\right)\,\mathrm dx \\ 
 &=\frac{3}{8}\sqrt{\frac{\pi}{2}}(\sin(2)+\cos(2))-\frac{1}{8}\sqrt{\frac{\pi}{6}}(\sin(6)+\cos(6)) \end{align*}$$

 where in the last line we've made use of the [Fresnel integrals](https://en.wikipedia.org/wiki/Fresnel_integral)

 $$\int_0^\infty\sin(x^2)\,\mathrm dx=\frac{1}{2}\sqrt{\frac{\pi}{2}}$$

 and

 $$\int_0^\infty\cos(x^2)\,\mathrm dx=\frac{1}{2}\sqrt{\frac{\pi}{2}}.$$