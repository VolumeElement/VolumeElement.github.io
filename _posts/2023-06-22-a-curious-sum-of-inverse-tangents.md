---
title: A Curious Sum of Inverse Tangents
# author: dxdydz
date: 2023-06-22 15:00:00 -0400
categories: [Calculus]
tags: [infinite series, infinite products]
math: True
pin: False
---

## Problem

Evaluate

$$\sum_{n=1}^\infty\text{arctan}\left(\frac{1}{8n^2}\right)$$

## Solution



We can compute this sum by considering it as the argument of an infinite product. Here the argument of the nth factor of the product is $-\text{arctan}(1/8n^2)$,

$$\begin{align*}\sum_{n=1}^\infty\text{arctan}\left(\frac{1}{8n^2}\right) &=-\text{arg}\prod_{n=1}^\infty\left(1-\frac{i}{8n^2}\right) \\  &= -\text{arg}\prod_{n=1}^\infty\left(1-\frac{\left(\sqrt{i/8}\right)^2}{n^2}\right)\\  &=-\text{arg}\frac{\sin\left(\pi\sqrt{i/8}\right)}{\pi\sqrt{i/8}},\qquad\text{by Euler's product for the sine} \\  &=-\text{arg}\left(\frac{(1-i)\sqrt{2}\cosh(\pi/4)}{\pi}+\frac{(1+i)\sqrt{2}\sinh(\pi/4)}{\pi}\right) \\  &=-\text{arctan}\left(\frac{\sinh(\pi/4)-\cosh(\pi/4)}{\sinh(\pi/4)+\cosh(\pi/4)}\right) \\ &= \text{arccot}\left(e^{\pi/2}\right).\end{align*}$$