---
title: A Double Sum with Fantastic Symmetry
# author: dxdydz
date: 2023-06-29 12:00:00 -0400
categories: [Calculus]
tags: [infinite series, integration, contour integration]
math: True
pin: False
---

The double sum

$$\sum_{a=1}^{\infty}\sum_{b=1}^{\infty} \frac{a^2b^2}{\sinh(\pi(a+b))}(-1)^{a+b}$$

was asked about on [math.se](https://math.stackexchange.com/questions/4622932), originally I tried evaluating this sum in a way that might make use of modular forms or the Dedekind eta function, but I found there was a wonderful method of evaluation that made use of a symmetry among poles along the real and imaginary axes in the complex plane. The factor $\csc(\pi z)$, originally introduced to account for the alternating sign in the sum, trades places with $\sinh(\pi z)$ along the imaginary axis to give twice the desired sum from the contour integral.

## Solution

We start by turning the doubly infintie series into a single infinite series. Collecting all $a,\,b$ that satisfy $a+b=n$ gives

$$\begin{align*}\sum_{a=1}^{\infty}\sum_{b=1}^{\infty} \frac{a^2b^2}{\sinh(\pi(a+b))}(-1)^{a+b} &= \sum_{n=2}^\infty\frac{(-1)^n}{\sinh(\pi n)}\sum_{k=1}^{n-1}k^2(n-k)^2 \\&= \frac{1}{30}\sum_{n=2}^\infty\frac{(n^5-n)(-1)^n}{\sinh(\pi n)} \\&= \frac{1}{60}\sum_{n\in\mathbb{Z}\setminus\left\{0\right\}}\frac{(n^5-n)(-1)^n}{\sinh(\pi n)}.\end{align*}$$

We now make use of the residue theorem to evaluate the above bilateral infinite series. Let $C_L$ be a positively oriented square contour of side length $L$ centered at $z=0$ with vertices at $z=(\pm1\pm i)L/2$. As $L\to\infty$, one may bound the integrals along the edges to show that

$$\begin{align}\lim_{L\to\infty}\frac{1}{2\pi i}\oint_{C_L}\frac{(z^5-z)}{60\sinh(\pi z)}\pi\csc(\pi z)\,\mathrm dz=0.\end{align}$$

(Details relevant to the above method may be seen [here](http://people.uncw.edu/hermanr/complex/summation-series-residue.pdf).) The integrand has poles at $\mathbb{Z}$ and $i\mathbb{Z}$, set minus $\pm1$ and $\pm i$, applying the residue theorem tells us

$$\begin{align}0 &= \underset{z=0}{\text{Res}}\left[\frac{(z^5-z)}{60\sinh(\pi z)}\pi\csc(\pi z)\right]+\sum_{n\in\mathbb{Z}\setminus\left\{0,\,\pm1\right\}}\underset{z=n}{\text{Res}}\left[\frac{(z^5-z)}{60\sinh(\pi z)}\pi\csc(\pi z)\right] \\&\qquad+\sum_{n\in \mathbb{Z}\setminus\left\{0,\,\pm1\right\}}\underset{z=in}{\text{Res}}\left[\frac{(z^5-z)}{60\sinh(\pi z)}\pi\csc(\pi z)\right] \\&=-\frac{1}{60\pi}+\frac{1}{60}\sum_{n\in\mathbb{Z}\setminus\left\{0,\,\pm1\right\}}\frac{(n^5-n)(-1)^n}{\sinh(\pi n)}+i\sum_{n\in \mathbb{Z}\setminus\left\{0,\,\pm1\right\}}\underset{z=n}{\text{Res}}\left[\frac{((iz)^5-iz)}{60\sinh(\pi iz)}\pi\csc(\pi iz)\right] \\&= -\frac{1}{60\pi}+\frac{1}{60}\sum_{n\in\mathbb{Z}\setminus\left\{0,\,\pm1\right\}}\frac{(n^5-n)(-1)^n}{\sinh(\pi n)}+\sum_{n\in\mathbb{Z}\setminus\left\{0,\,\pm1\right\}}\underset{z=n}{\text{Res}}\left[\frac{(z^5-z)}{60\sinh(\pi z)}\pi\csc(\pi z)\right] \\&= -\frac{1}{60\pi}+\frac{1}{30}\sum_{n\in\mathbb{Z}\setminus\left\{0,\,\pm1\right\}}\frac{(n^5-n)(-1)^n}{\sinh(\pi n)}.\end{align}$$

This implies that

$$\frac{1}{60}\sum_{n\in\mathbb{Z}\setminus\left\{0\right\}}\frac{(n^5-n)(-1)^n}{\sinh(\pi n)}=\frac{1}{120\pi}$$

or put differently,

$$\sum_{a=1}^{\infty}\sum_{b=1}^{\infty} \frac{a^2b^2}{\sinh(\pi(a+b))}(-1)^{a+b}=\frac{1}{120\pi}.$$