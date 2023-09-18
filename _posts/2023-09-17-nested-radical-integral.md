---
title: An Integral of a Nested Radical
# author: dxdydz
date: 2023-09-17 20:15:00 -0400
categories: [Calculus]
tags: [integration, nested radicals]
math: True
pin: False
---

## Problem

Evaluate

$$I=\int_{-1/2}^{1/2}\sqrt{1+x^2+\sqrt{1+x^2+x^4}}\,\mathrm dx.$$

## Solution

Before doing any calculus, we first need to denest the radical. We can try to find two polynomial functions $f$ and $g$ that satisfy

$$\sqrt{1+x^2+\sqrt{1+x^2+x^4}}=\sqrt{f}+\sqrt{g}.$$

Squaring each side, we get

$$1+x^2+\sqrt{1+x^2+x^4}=f+g+2\sqrt{fg}$$

and since we assumed both of the unknown functions to be polynomials we see that

$$f+g=1+x^2$$

and

$$4fg=1+x^2+x^4.$$

Solving this system of equations yields

$$f=\frac{1}{2}+\frac{x}{2}+\frac{x^2}{2}$$

and

$$g=\frac{1}{2}-\frac{x}{2}+\frac{x^2}{2}$$

so

$$I=\frac{1}{\sqrt{2}}\int_{-1/2}^{1/2}\left(\sqrt{1+x+x^2}+\sqrt{1-x+x^2}\right)\,\mathrm dx.$$

Now we may integrate using a hyperbolic substitution, $x=\sqrt{3}\sinh(u)/2-1/2$,

$$\int\sqrt{1+x+x^2}\,\mathrm dx =\frac{1}{4}(2x+1)\sqrt{1+x+x^2}+\frac{3}{8}\text{arcsinh}\left(\frac{2x+1}{\sqrt{3}}\right)+C.$$

The other integral is done similarly to get

$$\int\sqrt{1-x+x^2}\,\mathrm dx =\frac{1}{4}(2x-1)\sqrt{1-x+x^2}+\frac{3}{8}\text{arcsinh}\left(\frac{2x-1}{\sqrt{3}}\right)+C.$$

Putting it all together results in the final value

$$\int_{-1/2}^{1/2}\sqrt{1+x^2+\sqrt{1+x^2+x^4}}\,\mathrm dx=\frac{\sqrt{14}}{4}+\frac{3\sqrt{2}}{8}\text{arcsinh}\left(\frac{2\sqrt{3}}{3}\right).$$