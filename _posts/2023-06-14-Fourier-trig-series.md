---
title: Using log-trig Fourier Series
# author: dxdydz
date: 2023-06-14 22:00:00 -0400
categories: [Calculus]
tags: [integration, series]
math: True
pin: False
---

Fourier series for the natural logarithms of trigonometric functions can make quick work of some tricky integrals. In this post we cover two such examples.

## The Series

The needed Fourier series are

$$\ln(\sin(x))=-\ln(2)-\sum_{n=1}^\infty\frac{\cos(2nx)}{n}$$

and

$$\ln(\cos(x))=-\ln(2)-\sum_{n=1}^\infty(-1)^n\frac{\cos(2nx)}{n}.$$

The derivation of these is rather short and be found on [math.se](https://math.stackexchange.com/questions/292468/fourier-series-of-log-sine-and-log-cos).

## Problem 1

Evaluate

$$I=\int_0^{\frac{\pi}{2}}\frac{x\cdot\sin(x)}{\cos(x)+\sin(x)}\,\mathrm dx.$$

We can begin our attack by making the substitution $x\mapsto\frac{\pi}{2}-x$ so that

$$I=\frac{\pi}{2}\int_0^{\frac{\pi}{2}}\frac{\cos(x)}{\cos(x)+\sin(x)}\,\mathrm dx-\int_0^{\frac{\pi}{2}}\frac{x\cdot\cos(x)}{\cos(x)+\sin(x)}\,\mathrm dx.$$

Averaging this new representation of $I$ with the original one, we find that

$$I=\frac{\pi}{4}\int_0^{\frac{\pi}{2}}\frac{\cos(x)}{\cos(x)+\sin(x)}\,\mathrm dx+\frac{1}{2}\int_0^{\frac{\pi}{2}}x\cdot\frac{\sin(x)-\cos(x)}{\sin(x)+\cos(x)}\,\mathrm dx.$$

The $\int_0^{\frac{\pi}{2}}\frac{\cos(x)}{\cos(x)+\sin(x)}\,\mathrm dx$ integral may be easily evaluated to $\frac{\pi}{4}$ by making the substitution $x\mapsto\frac{\pi}{2}-x$ and doing a similar averaging trick. So

$$I=\frac{\pi^2}{16}+\frac{1}{2}\int_0^{\frac{\pi}{2}}x\cdot\frac{\sin(x)-\cos(x)}{\sin(x)+\cos(x)}\,\mathrm dx.$$

The remaining integral may be dealt with by integrating by parts. Let $u=x$ and $\mathrm dv=\frac{\sin(x)-\cos(x)}{\sin(x)+\cos(x)}\,\mathrm dx$ so

$$\int_0^{\frac{\pi}{2}}x\cdot\frac{\sin(x)-\cos(x)}{\sin(x)+\cos(x)}\,\mathrm dx=\underset{J}{\underbrace{\int_0^{\frac{\pi}{2}}\ln\left(\cos(x)+\sin(x)\right)\,\mathrm dx}}.$$

Then

$$\begin{align*}    J &= \int_0^{\frac{\pi}{2}}\ln\left(\sqrt{2}\sin\left(x+\frac{\pi}{4}\right)\right)\,\mathrm dx\\    &= \frac{\pi\ln(2)}{4}+\int_0^{\frac{\pi}{2}}\ln\left(\sin\left(x+\frac{\pi}{4}\right)\right)\,\mathrm dx\\    &= \frac{\pi\ln(2)}{4}+\int_0^{\frac{\pi}{2}}\left(-\ln(2)-\sum_{n=1}^\infty\frac{\cos\left(2n\left(x+\frac{\pi}{4}\right)\right)}{n}\right)\,\mathrm dx \\    &= -\frac{\pi\ln(2)}{4}-\sum_{n=1}^\infty\frac{1}{n}\left[\frac{\sin\left(\frac{\pi n}{2}\right)\cos(2nx)}{2n}+\frac{\cos\left(\frac{\pi n}{2}\right)\sin(2nx)}{2n}\right]\Bigg\vert_0^{\frac{\pi}{2}}\\    &= -\frac{\pi\ln(2)}{4}-\frac{1}{2}\sum_{n=1}^\infty\frac{\sin\left(\frac{2\pi n}{2}\right)-\sin\left(\frac{\pi n}{2}\right)}{n^2}\\    &=-\frac{\pi\ln(2)}{4}+\sum_{k=0}^\infty\frac{(-1)^k}{(2k+1)^2}\\    &= G-\frac{\pi\ln(2)}{4}.\end{align*}$$

where we have recognised the series for [Catalan's constant](https://en.wikipedia.org/wiki/Catalan%27s_constant) in the second to last line.

Putting it all together yields

$$\int_0^{\frac{\pi}{2}}\frac{x\cdot\sin(x)}{\cos(x)+\sin(x)}\,\mathrm dx=\frac{\pi^2}{16}+\frac{G}{2}-\frac{\pi}{8}\ln(2).$$

## Problem 2

This problem is comparitively straightforward,

$$\begin{align*} \int_0^{\pi/2}x\ln(\tan(x))\,\mathrm dx &= \int_0^{\pi/2}x\ln(\sin(x))\,\mathrm dx-\int_0^{\pi/2}x\ln(\cos(x))\,\mathrm dx \\ &= \int_0^{\pi/2}x\left(-\ln(2)-\sum_{n=1}^\infty\frac{\cos(2nx)}{n}\right)\,\mathrm dx + \int_0^{\pi/2}x\left(\ln(2)+\sum_{n=1}^\infty(-1)^n\frac{\cos(2nx)}{n}\right)\,\mathrm dx \\ &= -2\sum_{k=0}^\infty\frac{1}{2k+1}\int_0^{\pi/2}x\cos(2(2k+1)x)\,\mathrm dx,\,\text{terms of even index cancel} \\ &= -2\sum_{k=0}^\infty\frac{1}{2k+1}\left[\frac{(2(2k+1))x\sin((2(2k+1))x)+\cos((2(2k+1))x)}{(2(2k+1))^2}\right]\Bigg\vert_0^{\pi/2},\\&\qquad \text{integrate by parts with }u=x\text{ and }\mathrm dv=\cos(2(2k+1)x)\,\mathrm dx \\&= -2\sum_{k=0}^\infty\frac{1}{2k+1}\cdot\frac{-2}{4(2k+1)^2} \\&= \sum_{k=0}^\infty\frac{1}{(2k+1)^3} \\&= \sum_{n=1}^\infty\frac{1}{n^3}-\sum_{n=1}^\infty\frac{1}{(2n)^3} \\&= \zeta(3)-\frac{1}{8}\zeta(3) \\&= \frac{7}{8}\zeta(3).\end{align*}$$