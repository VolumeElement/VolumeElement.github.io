---
title: A Golden Dilogarithmic Integral
# author: dxdydz
date: 2023-06-14 9:27:00 -0400
categories: [Calculus]
tags: [integration]
math: True
pin: False
---

The following integral is due to Ramamnujan (or so I was told). I have not been able to find a reference for it, but I imagine this would have been how it was derived.

$$\begin{align*}    \int_0^1\frac{\ln\left(\frac{1+\sqrt{4x+1}}{2}\right)}{x}\,\mathrm dx &= \int_1^\phi\frac{(2u-1)\ln(u)}{u^2-u}\,\mathrm du,\qquad x=u^2-u\\    &= \int_1^\phi\left(\frac{\ln(u)}{u}+\frac{\ln(u)}{1-u}\right)\,\mathrm du\\    &= \left[\frac{\ln^2(u)}{2}-\text{Li}_2(1-u)\right]\Bigg\vert_1^\phi\\    &= \frac{\ln^2(\phi)}{2}-\text{Li}_2(\bar{\phi})\\    &= \frac{\pi^2}{15}.\end{align*}$$

Several [special values](https://people.mpim-bonn.mpg.de/zagier/files/doi/10.1007/978-3-540-30308-4_1/fulltext.pdf) (as seen on page 6 of Zagier's write-up) can be obtained from the functional equations mentioned on pages 8 and 9.