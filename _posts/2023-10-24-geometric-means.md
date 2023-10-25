---
title: A Limit of Geometric Means
# author: dxdydz
date: 2023-10-24 23:00:00 -0400
categories: [Calculus]
tags: [limits, integration]
math: True
pin: False
---

## Problem

Show that

$$\lim_{n\to\infty}\left(\sqrt[n+1]{(n+1)!}-\sqrt[n]{n!}\right)=\frac{1}{e}.$$

## Solution

First see that

$$\begin{align*}\sqrt[m]{m!} &= \exp\left(\frac{1}{m}\sum_{k=1}^m\ln(k)\right) \\&= \exp\left(\ln(m)+\frac{1}{m}\sum_{k=1}^m\ln\left(\frac{k}{m}\right)\right) \\&= m\exp\left(\frac{1}{m}\sum_{k=1}^m\ln\left(\frac{k}{m}\right)\right)\end{align*}$$

In the last line above, the sum contained in the exponential is a Riemann sum that monoronically decreases to

$$\int_0^1\ln(x)\,\mathrm dx=-1$$

so the function of interest must be bounded as follows

$$(n+1)\exp\left(\frac{1}{n+1}\sum_{k=1}^{n+1}\ln\left(\frac{k}{n+1}\right)\right)-n\exp\left(\frac{1}{n+1}\sum_{k=1}^{n+1}\ln\left(\frac{k}{n+1}\right)\right)<\sqrt[n+1]{(n+1)!}-\sqrt[n]{n!}<(n+1)\exp\left(\frac{1}{n}\sum_{k=1}^{n}\ln\left(\frac{k}{n}\right)\right)-n\exp\left(\frac{1}{n}\sum_{k=1}^{n}\ln\left(\frac{k}{n}\right)\right).$$

After cancelling this is

$$\exp\left(\frac{1}{n+1}\sum_{k=1}^{n+1}\ln\left(\frac{k}{n+1}\right)\right)<\sqrt[n+1]{(n+1)!}-\sqrt[n]{n!}<\exp\left(\frac{1}{n}\sum_{k=1}^{n}\ln\left(\frac{k}{n}\right)\right)$$

But we've already noted these Riemann sums converge to $-1$, so by the squeeze theorem we must have

$$\lim_{n\to\infty}\left(\sqrt[n+1]{(n+1)!}-\sqrt[n]{n!}\right)=\frac{1}{e}$$

as desired.