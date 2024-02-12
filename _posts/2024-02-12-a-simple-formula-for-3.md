---
title: A Simple Formula for 3
# author: dxdydz
date: 2024-02-12 15:10:00 -0400
categories: [Calculus]
tags: [integration, elliptic integrals]
math: True
pin: False
---

In a [previous post](https://volumeelement.github.io/posts/elliptic-integrals-and-cm/) we proved that

$$\begin{align*}\int_0^\alpha \frac{du}{\sqrt{1+u^4}}=\frac{3\Gamma^2\left(\frac{1}{4}\right)}{16\sqrt{\pi}}\tag{1}\end{align*}$$

where $\alpha=\sqrt{1+\sqrt{2}+\sqrt{2+2\sqrt{2}}}$. Here we will show that

$$\begin{align*}\int_0^\beta \frac{du}{\sqrt{1+u^4}}=\frac{\Gamma^2\left(\frac{1}{4}\right)}{16\sqrt{\pi}}\tag{2}\end{align*}$$

where $\beta=\sqrt{1+\sqrt{2}-\sqrt{2+2\sqrt{2}}}$, which actually ends up being much easier to do.

## Proof

We start by proving the following,

> **Fagnano's lemniscatic doubling theorem:**
>
> Let $0<s<\sqrt{\sqrt{2}-1}$, then
>
> $$\displaystyle{2\int_0^s\frac{\mathrm dx}{\sqrt{1-x^4}}=\int_0^t\frac{\mathrm dx}{\sqrt{1-x^4}}}$$
>
> where
>
> $$\displaystyle{t=\frac{2s\sqrt{1-s^4}}{1+s^4}.}$$
>
> $$\,$$

**Proof:**

First observe that

$$t'(s)=\frac{2(s^4+2s^2-1)(s^4-2s^2-1)}{(1+s^4)^2\sqrt{1-s^4}}$$

which is continuous and increasing on the interval $[0,\,\sqrt{\sqrt{2}-1}]$ where $\sqrt{\sqrt{2}-1}$ is the smallest solution of $t'(s)=0.$ We also have

$$1-t^4(s)=\frac{(s^4+2s^2-1)(s^4-2s^2-1)}{(1+s^4)^2}$$

therefore

$$\frac{\mathrm dt}{\sqrt{1-t^4(s)}}=2\frac{\mathrm ds}{\sqrt{1-s^4}}.$$

Integrating on the appropriate interval then yields the theorem.[^1] $\blacksquare$

> **Corollary:**
>
> $$\displaystyle{2\int_0^s\frac{\mathrm dx}{\sqrt{1+x^4}}=\int_0^t\frac{\mathrm dx}{\sqrt{1+x^4}}}$$
>
> where
>
> $$\displaystyle{t=\frac{2s\sqrt{1+s^4}}{1-s^4}.}$$
>
> $$\,$$

This can be easily shown by letting $x\mapsto e^{i\pi/4}x$ in Fagnano's theorem. $\blacksquare$

To derive $(2)$ first let $t=1$ then solve for $s$, from which we find that $s=\beta$. Then we can show $\int_0^1\frac{\mathrm dx}{\sqrt{1+x^4}}=\Gamma^3(1/4)/8$ (which can be proven using the [beta function](https://en.wikipedia.org/wiki/Beta_function)). As a consequence, we get an absurd expression for $3$ that only uses the numbers $0,\,1,\,2,$ and $4$.

$$\int_0^{\sqrt{1+\sqrt{2}+\sqrt{2+2\sqrt{2}}}}\frac{\mathrm dx}{\sqrt{1+x^4}}\Bigg/\int_0^{\sqrt{1+\sqrt{2}-\sqrt{2+2\sqrt{2}}}}\frac{\mathrm dx}{\sqrt{1+x^4}}=3$$

This quotient of integrals should have good applications in [nerd sniping](https://xkcd.com/356/).

<center><a href="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/Kurisu_Elliptic_Integral_Meme_2.png"><img src="https://raw.githubusercontent.com/VolumeElement/VolumeElement.github.io/main/images/Kurisu_Elliptic_Integral_Meme_2.png" alt="centered image" height="auto" width="450" title="source: github.com" /></a></center>

## References

[^1]: *Elliptic Functions Introduction Course*, Vladimir G. Tkachev, [https://users.mai.liu.se/vlatk48/teaching/lect2-agm.pdf](https://users.mai.liu.se/vlatk48/teaching/lect2-agm.pdf)