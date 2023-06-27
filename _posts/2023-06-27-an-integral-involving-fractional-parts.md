---
title: An Integral Involving Fractional Parts
# author: dxdydz
date: 2023-06-27 18:40:00 -0400
categories: [Calculus]
tags: [integration, infinite series, infinite products]
math: True
pin: False
---

## Problem

Evalaute

$$\int_1^\infty\frac{\left\{x\right\}-\frac{1}{2}}{x}\,\mathrm dx$$

where $\left\{x\right\}$ denotes the fractional part of $x$.

## Solution

First we may rewrite the integral as a series,

$$\begin{align*}\int_1^\infty\frac{\left\{x\right\}-\frac{1}{2}}{x}\,\mathrm dx &=\sum_{n=1}^\infty\int_n^{n+1}\frac{\left\{x\right\}-\frac{1}{2}}{x}\,\mathrm dx \\  &=\sum_{n=1}^\infty\int_0^1\frac{\left\{x+n\right\}-\frac{1}{2}}{x+n}\,\mathrm dx \\  &=\sum_{n=1}^\infty\int_0^1\frac{x-\frac{1}{2}}{x+n}\,\mathrm dx \\  &= \sum_{n=1}^\infty\int_0^1\left(1-\left(n+\frac{1}{2}\right)\frac{1}{x+n}\right)\,\mathrm dx \\  &=\sum_{n=1}^\infty\left(1+\left(n+\frac{1}{2}\right)\ln(n)-\left(n+\frac{1}{2}\right)\ln(n+1) \right ) \\  &= \ln\left(\prod_{n=1}^\infty\left(\frac{n}{n+1} \right )^{n+1/2}e \right ).\end{align*}$$

Examining the partial products yields the telescoping formula

$$\prod_{n=1}^m\left(\frac{n}{n+1} \right )^{n+1/2}e=\frac{m!e^m}{(m+1)^{m+1/2}}.$$

If we apply [Stirling's approximation](https://en.wikipedia.org/wiki/Stirling%27s_approximation) and take a limit we find that

$$\begin{align*}\lim_{m\to\infty}\prod_{n=1}^m\left(\frac{n}{n+1} \right )^{n+1/2}e &= \lim_{m\to\infty}\frac{m!e^m}{(m+1)^{m+1/2}} \\  &= \lim_{m\to\infty}\frac{\sqrt{2\pi m}\cdot m^m e^m}{e^m(m+1)^{m+1/2}} \\  &= \sqrt{2\pi}\lim_{m\to\infty}\sqrt{\frac{m}{m+1}}\left(\frac{m}{m+1} \right )^m\\  &= \sqrt{2\pi}\lim_{m\to\infty}\left(1-\frac{1}{m+1} \right )^m\\  &= \sqrt{2\pi}\lim_{m\to\infty}\left(1-\frac{1}{m+1} \right )^{m+1}\left(1-\frac{1}{m+1} \right )^{-1} \\ &= \sqrt{2\pi}\lim_{m\to\infty}\left(1-\frac{1}{m+1} \right )^{m+1} \\ &= \frac{\sqrt{2\pi}}{e}.\end{align*}$$

So

$$\int_1^\infty\frac{\left\{x\right\}-\frac{1}{2}}{x}\,\mathrm dx=\ln\left(\frac{\sqrt{2\pi}}{e}\right).$$