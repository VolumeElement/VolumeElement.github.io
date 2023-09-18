---
title: A Geometric Differential Equation
# author: dxdydz
date: 2023-09-18 18:30:00 -0400
categories: [Calculus]
tags: [differential equations, geometric calculus]
math: True
pin: False
---

## Problem

For $x$ such that $f(x)\neq0$, define the $*$-derivative of $f$ at $x$ as

$$f^*(x)=\lim_{h\to0}\left(\frac{f(x+h)}{f(x)}\right)^{\frac{1}{h}}.$$

What is the general solution to the $*$-differential equation

$$f^*(x)f^{**}(x)=f(x)?$$

## Solution

First we rewrite $f^*(x)$,

$$\begin{align*}
\lim_{h\to0}\left(\frac{f(x+h)}{f(x)}\right)^{\frac{1}{h}} &= \lim_{h\to0}\left(1+\frac{f(x+h)-f(x)}{f(x)}\right)^{\frac{1}{h}} \\
&= \lim_{h\to0}\left(1+\frac{f(x+h)-f(x)}{f(x)}\right)^{\frac{f(x)}{f(x+h)-f(x)}\cdot\frac{f(x+h)-f(x)}{h}\cdot\frac{1}{f(x)}} \\
&= \lim_{h\to0}\left(\left(1+\frac{f(x+h)-f(x)}{f(x)}\right)^{\frac{f(x)}{f(x+h)-f(x)}}\right)^{\frac{f(x+h)-f(x)}{h}\cdot\frac{1}{f(x)}}.
\end{align*}$$

Now note that the piece in the big parentheses ends up being the limit defintion for $e$ and the power outside of it becomes $\mathrm d/\mathrm dx\ln(f(x))$ so

$$f^*(x)=\exp\left(\frac{\mathrm d}{\mathrm dx}\ln(f(x))\right).$$

It is easy to show that

$$f^{**}(x)=\exp\left(\frac{\mathrm d^2}{\mathrm dx^2}\ln(f(x))\right)$$

and in general,

$$f^{*(n)}(x)=\exp\left(\frac{\mathrm d^n}{\mathrm dx^n}\ln(f(x))\right).$$

### Solving the original problem

Now that we know more about the $*$-derivative, we may restate the original equation as

$$\exp\left(\frac{\mathrm d}{\mathrm dx}\ln(f(x))\right)\exp\left(\frac{\mathrm d^2}{\mathrm dx^2}\ln(f(x))\right)=f(x),$$

or upon removing the exponentials,

$$\frac{\mathrm d}{\mathrm dx}\ln(f(x))+\frac{\mathrm d^2}{\mathrm dx^2}\ln(f(x))=\ln(f(x)).$$

So we may renconsider this as trying to find the soltuion to

$$g''(x)+g'(x)-g(x)=0$$

where $g(x)=\ln(f(x))$. We may solve this using the characteristic equation

$$r^2+r-1=0$$

which has roots

$$r_1=-\frac{1+\sqrt{5}}{2},\,-\frac{1-\sqrt{5}}{2}.$$

So

$$g(x)=c_1e^{-\phi x}+c_2e^{-\bar{\phi}x}$$

where $\phi$ is the golden ratio and $\bar{\phi}$ is the conjugate golden ratio. Translating back to $f$ we conclude that

$$f(x)=\exp\left(c_1e^{-\phi x}+c_2e^{-\bar{\phi}x}\right).$$

## Further reading

The defintion of $f^*(x)$ given in the original problem is the [geometric derivative](https://en.wikipedia.org/wiki/Product_integral). There is also a geometric integral given by

$$\lim_{\Delta x \to 0} \prod{f(x_i)^{\Delta x}}=\prod_a^b f(x)^{\mathrm dx}$$

and playing similar games with limits gives a formula in terms of the  Riemann integral

$$\prod f(x)^{\mathrm dx}=\exp\left(\int\ln(f(x))\,\mathrm dx\right).$$

One may also check that

$$\left(\prod f(x)^{\mathrm dx}\right)^*=f(x)$$

as we'd would hope!