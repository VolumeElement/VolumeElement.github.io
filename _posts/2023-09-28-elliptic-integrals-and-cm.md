---
title: Elliptic Integrals and CM Elliptic Curves
# author: dxdydz
date: 2023-09-28 09:00:00 -0400
categories: [Number Theory]
tags: [elliptic curves, complex multiplication, integration, sage, python]
math: True
pin: False
---

A long time ago, I saw [an intriguing question](https://www.tapatalk.com/groups/integralsandseries/weierstrass-p-function-exercise-t749.html) posed by Shobhit, asking to show that

$$\begin{align*}\int_0^\alpha \frac{du}{\sqrt{1+u^4}}=\frac{3\Gamma^2\left(\frac{1}{4}\right)}{16\sqrt{\pi}}\tag{1}\end{align*}$$

where $\alpha=\sqrt{1+\sqrt{2}+\sqrt{2+2\sqrt{2}}}$. I played with this problem off and on for a few years, but as I was unfamiliar with elliptic curves I did not make much progress on it other than noting it was a rational multiple of

$$\int_0^1\frac{1}{\sqrt{1+u^4}}\,\mathrm du=\frac{\Gamma^2\left(\frac{1}{4}\right)}{8\sqrt{\pi}},$$

which I found to be so strange that I thought it could not be a mere coincidence. It turns out that it's not a coincidence and is really a consequence of

$$\begin{align*}E/\mathbb{Q}:\,y^2=x^3-4x\tag{2}\end{align*}$$

being an elliptic curve with complex multiplication. Understanding this integral and how to create similar identities was one of my white whales and it feels great to have caught it.

## Solution

First we note that $v^2=1+u^4$ has genus $1$ and a rational point $(0,\,1)$, hence it is an elliptic curve. So we may transform the curve

$$E_0/\mathbb{Q}:\,v^2=1+u^4$$

with the mapping

$$x=\frac{2v+2}{u^2},\,y=\frac{4v+4}{u^3}$$

and its inverse $u=2x/y,\,v=-1+2x^3/y^2$ which takes us to the elliptic curve

$$E/\mathbb{Q}:\,y^2=x^3-4x$$

and back. Details on this mapping and how it generalizes may be seen in Washington[^1], pages 37 and 38. This map nets us the equality

$$\begin{align*}\int_0^\alpha \frac{du}{\sqrt{1+u^4}}=\int_{\alpha'}^\infty\frac{\mathrm dx}{\sqrt{x^3-4x}}\tag{3}\end{align*}$$

where

$$\alpha'=2\left(1+\sqrt{2}-\sqrt{2+2\sqrt{2}}\right)\left(1+\sqrt{6+4\sqrt{2}+2\sqrt{14+10\sqrt{2}}}\right).$$

Things look worse but it actually gets better from here on out. The minimal polynomial of $\alpha'$ ends up being

$$p(x)=x^8-16x^7-48x^6-64x^5+608x^4+256x^3-768x^2+1024x+256$$

and running the command `E = EllipticCurve('64a1'); E.division_polynomial(8).factor()` in Sage shows that $p(x)$ is indeed a factor of the eighth [division polynomial](https://en.wikipedia.org/wiki/Division_polynomials) $\psi_8(x)$ associated to $E$, hence $\alpha'$ must be the $x$ coordinate of a point of order $8$. It's easy to see that

$$\begin{align*}\int_2^{\alpha'}\frac{\mathrm dx}{\sqrt{x^3-4x}}+\int_{\alpha'}^\infty\frac{\mathrm dx}{\sqrt{x^3-4x}}=\int_2^\infty\frac{\mathrm dx}{\sqrt{x^3-4x}}\tag{4}\end{align*}$$

and looking at the factors of $\psi_8(x)$ shows, somewhat unsuprisingly, that $x=2$ is also an element of $E[8]$, the order $8$ division points of $E$. This second observation leads us to ask if there is a multiplication by by $n$ map, in the same style as described by pisco[^2], that turns the point $\alpha'$ into something *simple* and maps another integral bound in $(4)$ to something that is also easy to deal with. After a lot of pondering, the first canidate that came to mind is applying a $4$-isogeny

$$(x,\,y)\mapsto(f_1(x),\,f_2(x)):\,E\rightarrow E$$

to the leftmost integral in $(4)$. The function $f_1(x)$ may be expressed as $f_1(x)=(g\circ g)(x)$ where $g$ corresponds to the change in $x$ coordinate given by the $2$-isogeny or [point doubling](https://en.wikipedia.org/wiki/Elliptic_curve_point_multiplication#Point_addition) formula

$$g(x)=\frac{3x^2-4}{4(x^3-4x)}-2x.$$

Composing $g$ with itself results in the the rational function

$$g(t)=\frac{(256+1280t^2-416t^4+80t^6+t^8)^2}{16t(t^2-4)(4+t^2)^2(16-24t^2+t^4)^2}$$

that maps $g(2)=\infty$ and $g(\alpha')=2$. This leads us to use the utterly depraved $u$-substitution

$$\int_2^{\alpha'}\frac{\mathrm dx}{\sqrt{x^3-4x}}=-\frac{1}{4}\int_\infty^2\frac{\mathrm dt}{\sqrt{t^3-4t}},\,x=g(t)$$

which is the mapping of the form

$$\begin{align*}4\int_2^{\alpha'} \omega \cong \int_{\infty}^2\omega\tag{5}\end{align*}$$

described in the previously linked math.se page. Using this on the leftmost integral in $(4)$ results in

$$\int_{\alpha'}^\infty\frac{\mathrm dx}{\sqrt{x^3-4x}}=\frac{3}{4}\int_2^\infty\frac{\mathrm dx}{\sqrt{x^3-4x}}.$$

The righthand integral in the above equality is very easy to evaluate in terms of the beta function,

$$\begin{align*}\int_2^\infty\frac{\mathrm dx}{\sqrt{x^3-4x}} &= \frac{1}{\sqrt{2}}\int_1^\infty\frac{\mathrm dx}{\sqrt{x^3-x}},\,x\mapsto 2x \\
&=\frac{1}{2\sqrt{2}}\int_0^1 
\frac{\mathrm dx}{x^{3/4}(1-x)^{1/2}},\,x\mapsto x^{-1/2} \\
&= \frac{1}{2\sqrt{2}}\text{B}\left(\frac{1}{4},\,\frac{1}{2}\right) \\
&= \frac{\Gamma^2\left(\frac{1}{4}\right)}{4\sqrt{\pi}}.  \end{align*}$$

Therefore

$$\begin{align*}\int_{\alpha'}^\infty\frac{\mathrm dx}{\sqrt{x^3-4x}}=\frac{3\Gamma^2\left(\frac{1}{4}\right)}{16\sqrt{\pi}}\end{align*}$$

and recalling $(3)$ tells us

$$\int_0^\alpha \frac{du}{\sqrt{1+u^4}}=\frac{3\Gamma^2\left(\frac{1}{4}\right)}{16\sqrt{\pi}}$$

which is what we had set out to confirm!

## The Chowla-Selberg formula

Why is it that any of the above integrals have such nice closed forms in terms of gamma functions at all? Let $\omega_E$ be a non-zero differential for $E$ (an elliptic curve with [complex multiplication](https://en.wikipedia.org/wiki/Complex_multiplication)) over the algebraic numbers and let

$$b_k=\sqrt{\pi}\prod_{a=1}^{d-1}\Gamma^{\frac{w\chi(a)}{4h}}\left(\frac{a}{d}\right)$$

where $\chi$ is the Dirichlet character modulo $d$ associated to $k$, $h$ is the class number of $k$, and $w$ is the order of the group of units of $k$. Chowla and Selberg showed that the ratio $\omega_E/b_k$ is always an algebraic number.[^3] So we see that integrals of the form $\int\omega_E$ which yield periods of elliptic curves are expressable as a quotient of gamma functions times an element of $\bar{\mathbb{Q}}$.

Together with the fact that $n$-isogenies have equivalences of the form given in $(5)$ up to an element of $H_1(E,\mathbb{Z})$ it should be of no suprise that any integral equivalent to a period under some isogeny should be expressable in terms of gamma functions. And just as a sanity check, the elliptic curve in $(2)$ does indeed have complex multiplication by the maps

$$(x,\,y)\mapsto\left(-x,\,\pm iy\right)$$

so the elliptic curve $E_0/\mathbb{Q}:\,v^2=1+u^4$ related to $(1)$ also has complex multiplication (following from the maps provided from Washinton) and fits this heuristic.

## Finding integrals quickly with Sage

Using Sagemath (and on occasion the Chowla-Selberg formula) we can quickly calculate find canidate bounds for elliptic integrals. As done before, we can pick a CM elliptic curve by its [Cremona label](https://www.lmfdb.org/knowledge/show/ec.q.cremona_label), run the command `E = EllipticCurve(<cremona label>)`, then use `E.division_polynomial(n)` to produce the $n$th division polynomial to pick possible $x$ values from. Doing so, one can produce a multitude of identitites similar to that which we have already seen.

$$\int _\alpha^\infty\frac{\mathrm dx}{\sqrt{x^3-x}}=\frac{\Gamma^2\left(\frac{1}{4} \right )}{3\sqrt{2\pi}},\,\alpha=\sqrt{1+\frac{2\sqrt{3}}{3}}$$

$$\int _0^\alpha\frac{\mathrm dx}{\sqrt{x-x^3}}=\frac{\Gamma^2\left(\frac{1}{4} \right )}{3\sqrt{2\pi}},\,\alpha=\sqrt{2\sqrt{3}-3}$$

$$\int_0^\alpha \frac{\mathrm dx}{\sqrt{x^3+1}}=\frac{2\Gamma^3\left(\frac{1}{3}\right)}{5\pi\sqrt{3}\sqrt[3]{2}},\,\alpha=\sqrt[3]{9\sqrt{5}-19+3\sqrt{78-\frac{174}{\sqrt{5}}}}$$

$$\int_0^{\sqrt{3}-1} \frac{\mathrm dx}{\sqrt{x^3+1}}=\frac{\Gamma^3\left(\frac{1}{3}\right)}{4\pi\sqrt{3}\sqrt[3]{2}}$$

$$\int_0^2 \frac{\mathrm dx}{\sqrt{x^3+1}}=\frac{\Gamma^3\left(\frac{1}{3}\right)}{2\pi\sqrt{3}\sqrt[3]{2}}$$

$$\int_0^\alpha\frac{\mathrm dx}{\sqrt{x-x^3}} = \frac{\Gamma^2\left(\frac{1}{4}\right)}{5\sqrt{2\pi}},\,\alpha=\sqrt{6\sqrt{5}-13-2\sqrt{85-38\sqrt{5}}}$$

$$\int_\alpha^1\frac{\mathrm dx}{\sqrt{x-x^3}} = \frac{\Gamma^2\left(\frac{1}{4}\right)}{3\sqrt{2\pi}},\,\alpha=1+\sqrt{3}-\sqrt{3+2\sqrt{3}}$$

$$\int_0^{\sqrt{2}} \frac{\mathrm dx}{\sqrt{x^3+3x^2+2x}} = \frac{\Gamma^2\left(\frac{1}{4}\right)}{4\sqrt{2\pi}}$$

$$\int_0^{1/7}\frac{\mathrm dx}{\sqrt{x-35x^3-98x^4}}=\frac{\Gamma\left(\frac{1}{7}\right)\Gamma\left(\frac{2}{7}\right)\Gamma\left(\frac{4}{7}\right)}{4\pi\sqrt{7}}$$

$$\int_0^\alpha\frac{\mathrm dx}{\sqrt{x-35x^3-98x^4}}=\frac{\Gamma\left(\frac{1}{7}\right)\Gamma\left(\frac{2}{7}\right)\Gamma\left(\frac{4}{7}\right)}{8\pi\sqrt{7}},\,\alpha=\frac{4\sqrt{7}}{63}-\frac{1}{9}$$

$$\int_0^{4\sqrt{7}}\frac{\mathrm dx}{\sqrt{x^3+21x^2+112x}}=\frac{\Gamma\left(\frac{1}{7}\right)\Gamma\left(\frac{2}{7}\right)\Gamma\left(\frac{4}{7}\right)}{8\pi\sqrt{7}}$$

$$\int_0^\alpha\frac{\mathrm dx}{\sqrt{x-35x^3-98x^4}}=\frac{\Gamma\left(\frac{1}{7}\right)\Gamma\left(\frac{2}{7}\right)\Gamma\left(\frac{4}{7}\right)}{6\pi\sqrt{7}},\,\alpha=\frac{\sqrt{\frac{7}{3}}}{3+\sqrt{6+3\sqrt{21}}}$$

$$\int_0^\alpha\frac{\mathrm dx}{\sqrt{x-35x^3-98x^4}}=\frac{\Gamma\left(\frac{1}{7}\right)\Gamma\left(\frac{2}{7}\right)\Gamma\left(\frac{4}{7}\right)}{12\pi\sqrt{7}},\,\alpha=-\frac{7}{47}+\frac{6}{47}\sqrt{\frac{3}{7}}+\frac{1}{2}\sqrt{\frac{416}{2209}\sqrt{\frac{3}{7}}-\frac{1392}{15463}}$$

## References

[^1]: *Elliptic Curves, Number Theory, and Cryptography*, Lawrence C. Washington

[^2]: Prove $\int_0^2 \frac{dx}{\sqrt{1+x^3}}=\frac{\Gamma\left(\frac{1}{6}\right)\Gamma\left(\frac{1}{3}\right)}{6\Gamma\left(\frac{1}{2}\right)}$, [https://math.stackexchange.com/questions/3781324/prove-int-02-fracdx-sqrt1x3-frac-gamma-left-frac16-right-ga](https://math.stackexchange.com/questions/3781324/prove-int-02-fracdx-sqrt1x3-frac-gamma-left-frac16-right-ga)

[^3]: *On the periods of abelian integrals and a formula of Chowla and Selberg*, Benedict H. Gross, [https://doi.org/10.1007/BF01390273](https://doi.org/10.1007/BF01390273)