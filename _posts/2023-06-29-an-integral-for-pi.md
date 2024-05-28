---
title: An Integral for pi
# author: dxdydz
date: 2023-06-29 12:40:00 -0400
categories: [Calculus]
tags: [integration, infinite series]
math: True
pin: False
---

## Problem

Evaluate

$$-\int_0^\infty\frac{\ln(\cos^2(x))}{x^2}\,\mathrm dx.$$

## Solution

Let

$$I=\int_0^\infty\frac{\ln(\cos^2(x))}{x^2}\,\mathrm dx$$

so

$$\begin{align*}I &=\sum_{n=0}^\infty\int_{2\pi n}^{2\pi(n+1)}\frac{\ln(\cos^2(x))}{x^2}\,\mathrm dx \\  &=\sum_{n=0}^\infty\int_0^{2\pi}\frac{\ln(\cos^2(t+2\pi n))}{(t+2\pi n)^2}\,\mathrm dt,\;x=t+2\pi n \\  &=\int_0^{2\pi}\ln(\cos^2(t))\sum_{n=0}^\infty\frac{1}{(t+2\pi n)^2}\,\mathrm dt,\;\text{monotone convergence} \\  &=\frac{1}{4\pi^2}\int_0^{2\pi}\ln(\cos^2(t))\psi_1\left(\frac{t}{2\pi} \right )\,\mathrm dt\end{align*}$$

where $\psi_1(z)$ denotes the trigamma function. In the last integral in the above, we make the substitution $t\mapsto 2\pi-t$ to get

$$\frac{1}{4\pi^2}\int_0^{2\pi}\ln(\cos^2(t))\psi_1\left(\frac{t}{2\pi} \right )\,\mathrm dt=\frac{1}{4\pi^2}\int_0^{2\pi}\ln(\cos^2(t))\psi_1\left(1-\frac{t}{2\pi} \right )\,\mathrm dt.$$

We take the average of these two integrals,

$$\begin{align*}I &=\frac{1}{8\pi^2}\int_0^{2\pi}\ln(\cos^2(t))\left( \psi_1\left(\frac{t}{2\pi} \right )+\psi_1\left(1-\frac{t}{2\pi} \right )\right )\,\mathrm dt \\  &= \frac{1}{8}\int_0^{2\pi}\frac{\ln(\cos^2(t))}{\sin^2\left(\frac{t}{2} \right )}\,\mathrm dt\end{align*}$$

where the last line follows from the reflection formula for the trigamma function.

Then

$$\begin{align*}\frac{1}{8}\int_0^{2\pi}\frac{\ln(\cos^2(t))}{\sin^2\left(\frac{t}{2}\right)}\,\mathrm dt &= \frac{1}{4}\int_0^{2\pi}\frac{\ln(\cos^2(t))}{1-\cos(t)}\,\mathrm dt \\ &= \frac{1}{2}\int_0^\pi\frac{\ln(\cos^2(t))}{1-\cos(t)}\,\mathrm dt \\ &= \frac{1}{2}\int_{-1}^1\frac{\ln(u^2)}{\sqrt{1-u^2}}\cdot\frac{\mathrm du}{1-u},\qquad u=\cos(t) \\ &= \frac{1}{2}\int_{-1}^0\frac{\ln(u^2)}{\sqrt{1-u^2}}\cdot\frac{\mathrm du}{1-u}+\frac{1}{2}\int_0^1\frac{\ln(u^2)}{\sqrt{1-u^2}}\cdot\frac{\mathrm du}{1-u}\\ &= -\frac{1}{2}\int_0^{-1}\frac{\ln(u^2)}{\sqrt{1-u^2}}\cdot\frac{\mathrm du}{1-u}+\frac{1}{2}\int_0^1\frac{\ln(u^2)}{\sqrt{1-u^2}}\cdot\frac{\mathrm du}{1-u}\\ &= \frac{1}{2}\int_0^1\frac{\ln(u^2)}{\sqrt{1-u^2}}\cdot\frac{\mathrm du}{1+u}+\frac{1}{2}\int_0^1\frac{\ln(u^2)}{\sqrt{1-u^2}}\cdot\frac{\mathrm du}{1-u}, \\ &\qquad u\mapsto -u \\ &= \int_0^1\frac{\ln(u^2)}{(1-u^2)^{3/2}}\mathrm du \\ &= \frac{1}{2}\int_0^1\frac{\ln(v)}{v^{1/2}(1-v)^{3/2}}\,\mathrm dv,\qquad v=u^2 \\ &= \frac{1}{2}\lim_{\alpha\to1/2^+}\frac{\mathrm d}{\mathrm d \alpha}\int_0^1\frac{v^{\alpha-1}}{(1-v)^{3/2}}\,\mathrm dv \\ &= \frac{1}{2}\lim_{\alpha\to1/2^+}\frac{\mathrm d}{\mathrm d \alpha}\frac{\Gamma(\alpha)\Gamma(-1/2)}{\Gamma(\alpha-1/2)},\;\text{Euler beta function}\\ &= -\sqrt{\pi}\lim_{\alpha\to1/2^+}\frac{\Gamma(\alpha)(\psi(\alpha)-\psi(\alpha-1/2))}{\Gamma(\alpha-1/2)}, \\ &\qquad \text{where }\psi(z)\text{ is the digamma function}\\ &=-\sqrt{\pi}\cdot\sqrt{\pi}\\ &=-\pi.\end{align*}$$

In the last limit we made use of $\psi(\alpha)-\psi(\alpha-1/2)$ and $\Gamma(\alpha-1/2)$ are both $\sim1/\alpha$ for $\alpha\sim1/2$.