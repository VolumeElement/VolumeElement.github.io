---
title: Triangles and Hilbert's Theorem 90
# author: dxdydz
date: 2023-07-31 21:30:00 -0400
categories: [Number Theory]
tags: [Galois theory, Galois cohomology, field theory, Diophantine equations]
math: True
pin: False
---

It has been known since the time of the Babylonians that it is possible to parametrize all primitive<sup>1</sup> Pythagorean triples using a rather simple collection of expressions <code>&#8212;</code>  their understanding of this is recorded on [Plimpton 322](https://en.wikipedia.org/wiki/Plimpton_322). A fantastic geometric derivation of the same parametrization was also discovered later in ancient Greece. Consider a circle of unit radius centered at the origin and a line of rational slope passing through the point $(-1,\,0)$.

<center><a href="https://imgur.com/a/h07jx0w"><img src="https://i.imgur.com/auWDssN.png" alt="centered image" height="auto" width="367" title="source: imgur.com" /></a></center>

$$x^2+y^2=1,\,b(x+1)/a=y$$

Here we take $a$ and $b$ to be two coprime, positive integers with $a>b$. If we find the intersection of these two curves we get the obvious point of intersction, $(1,\,0)$, and the point

$$\left(\frac{a^2-b^2}{a^2+b^2},\,\frac{2ab}{a^2+b^2}\right).$$

Because this point is a solution to $x^2+y^2=1$, we may plug this point in and clear the denomiators to show that $X=a^2-b^2$, $Y=2ab$, $Z=a^2+b^2$ is a solution to $X^2+Y^2=Z^2$, i.e. it's a Pythagorean triple. In fact, as we vary $a$ and $b$ through all such pairs of coprime integers we get all primitive Pythagorean triples. To see this, note that in any primitive Pythagorean triple either $X$ or $Y$ must be even, suppose $Y$ is even so that $Y=2n$, then we have

$$4n^2=Z^2-X^2$$

which means

$$n^2=\frac{Z-X}{2}\cdot\frac{Z+X}{2}.$$

Since we assumed this was a primitive Pythagorean triple we have $\text{gcd}(X,\,Z)=1$, so $\text{gcd}((Z-X)/2,\,(Z+X)/2)=1$ as well. Since both of these factors are coprime and they divide $n^2$, they must also be perfect squares, so we may set

$$a^2=\frac{Z-X}{2}$$

and

$$b^2=\frac{Z+X}{2}.$$

It follows that $Y=2ab$. Solving the above pair of equations for $X$ and $Z$ shows that $X=a^2-b^2$ and $Z=a^2+b^2$, so every Pythagorean triple may be written in this way.

<sup>1: Primitive meaning all values in the solution are coprime.</sup>

### Another derivation

We will now prove the same result with the titular theorem.

> **Hilbert's theorem 90:** Given a field extension $L/K$, if $\text{Gal}(L/K)$ is cyclic with generator $\sigma$, and $\alpha\in L$ with $N_{L/K}(\alpha)=1$ then there is a $\beta\in L$ such that $\alpha=\beta/\sigma(\beta)$.

In order to parametrize all Pythagorean triples we may take our base field to be $\mathbb{Q}$ and our extension to be $\mathbb{Q}(i)$. Since $\text{Gal}(\mathbb{Q}(i)/\mathbb{Q})$ is cyclic and has generator $\sigma(\alpha)=\bar{z}$, it follows that every element $\alpha\in\mathbb{Q}(i)$ with $N(\alpha)=1$ can be written in terms of some $\beta=a+ib$ as

$$\begin{align*}\alpha &=\frac{\beta}{\sigma(\beta)} \\  &=\frac{a+ib}{a-ib} \\  &=\frac{a^2-b^2}{a^2+b^2}+i\frac{2ab}{a^2+b^2}. \\ \end{align*}$$

But since we picked $\alpha$ to have norm $1$, we also have

$$\left(\frac{a^2-b^2}{a^2+b^2}\right)^2+\left(\frac{2ab}{a^2+b^2}\right)^2=1$$

and clearing the denominators leaves us with the same parametrization as before

$$(a^2-b^2)^2+(2ab)^2=(a^2+b^2)^2.$$

## Galois cohomology and theorem 90

So where does this theorem come from? Hilbert's theorem 90 can be seen as a consequence of the fact that the $1\text{st}$ cohomology group is trivial*,

$$H^1(G,\,L^\times)=0.$$

Deciphering what this actually means was my initial motivation to understand Galois cohomology and cohomology in general. For a while I have been aware that Galois cohomology is an indispensable tool in modern number theory as it has the power to extract algebraic information about Galois groups that is normally veiled. One major place it shows up is in class field theory, which is another basic element of the modern number theorist's toolkit (and is something else I have been tackling).

The following notes in this section are primarily assembled from [^1] and [^2]. I found [^1] to be a fantastic resource as it introduces the topic in, what was for me, a familiar setting.

*Here $0$ represents the trivial group.

### Basics of group cohomology

We'll be needing an understanding of what is called the $1\text{st}$ cohomology group. As a vague prelude to where we're going, we are interested in the fixed points of certain group actions which I'll attempt to elucidate.

Let $M$ be an abelian group and consider the group action of $G$ on $M$ as a $G$-module. We will denote the action of $\sigma\in G$ on $m\in M$ as $\sigma\cdot m$. One of the simplest objects related to fixed points we may study is the collection of points that are fixed under all actions of $G$,

$$M^G=\left\{m\in M\,|\,\forall \sigma\in G,\,\sigma\cdot m=m\right\}.$$

It's also not hard to see that $M^G$ is a group, as $0\in M$ is always a fixed point and $\sigma\cdot(m+n)=\sigma\cdot m+\sigma\cdot n$. The $0\text{th}$ cohomology group is simply

$$H^0(G,\,M)\overset{\text{def}}{=}M^G,$$

but this will not be our main focus. Instead, to get to the main point of interest, we will need to define some new objects.

> **Defintion 1:** A $1$-cocycle is a map $\phi:\,G\to M$ such that $\phi(\sigma\tau)=\phi(\sigma)+\sigma\cdot\phi(\tau)$ for all $\sigma,\,\tau\in G.$

The collection of all such $\phi$ forms a group $Z^1(G,\,M)$ under the operation

$$(\phi_1+\phi_2)(\sigma)=\phi_1(\sigma)+\phi_2(\sigma).$$

> **Defintion 2:** A $1$-coboundary is a map $\psi:\,G\to M$ such that, for some fixed $m\in M$, $\psi(\sigma)=\sigma\cdot m-m$ for all $\sigma\in G$.

All of the $\psi$ also form a group, $B^1(G,\,M)$, under the same style of addition rule as described above. Note that every $1$-coboundary is also a $1$-cocycle. To see this, consider that

$$\begin{align*}\psi(\sigma\tau) &=(\sigma\tau)\cdot m-m \\  &=(\sigma\tau)\cdot m-\sigma\cdot m+\sigma\cdot m-m \\  &= \sigma\cdot(\tau\cdot m-m)+\sigma\cdot m-m \\ &= \psi(\sigma)+\sigma\cdot\psi(\tau).\end{align*}$$

So $\psi$ satisfies the relation required of $1$-cocycles and we have the inclusion of groups

$$B^1(G,\,M)\subseteq Z^1(G,\,M).$$

These groups are both abelian, so we may take their quotient,

$$H^1(G,\,M)\overset{\text{def}}{=}Z^1(G,\,M)/B^1(G,\,M),$$

and this is the $1\text{st}$ cohomology group.

### Intuition for $H^1(G,\,M)$

What kind of information does $H^1(G,\,M)$ tell us? A hint is in the construction of $B^1(G,\,M)$. Suppose that $N$ is a sub $G$-module of the $G$-module M and consider the action of $G$ on the quotient module $M/N$. If we pick some fixed point $[p]\in M/N$ we have that it satisfies

$$\sigma\cdot[p]-[p]=[0]$$

and for the representitive $p\in M$ we have that the coset of $\sigma\cdot p-p\,\text{mod}\,N$ is [0].  So we have $\sigma\cdot p-p\in N$, this element is only $0$ if $p\in M$ is a fixed point under the action of $G$, so this means the maps $\psi(\sigma)=\sigma\cdot p-p$ provide a measurement of how bad a point $[p]\in M/N$ fails at remaining fixed under the lift to $p\in M$.

To such a $[p]$ we may associate a unique $1$-cocycle (unique modulo $N$) $\phi(\sigma)=\sigma\cdot p-p$. Since a $1$-cocycle can only be a $1$-coboundry when there is a $q\in N$ such that $\phi(\sigma)=\sigma\cdot q-q$, i.e.

$$\begin{align*}\sigma\cdot(p-q) &= \sigma\cdot p-\sigma\cdot q\\  &=p-q, \\ \end{align*}$$

so $p-q$ is a fixed point in $M$, this means the obstruction to fixed points under the lift $M/N\to M$ is tied to the existence of nontrivial elements in $H^1(G,\,M)$. [^3] Put differently, if $H^1(G,\,M)=0$ then there is no obstruction to lifting fixed points.

### Proving theorem 90

We're now ready to prove the main theorem. Consider $L^\times$ as a $G$-module where $G=\text{Gal}(L/K)$. A map $\phi$ is a $1$-cocycle in $Z^1(G,\,L^\times)$ if, by definition<sup>2</sup>,

$$\phi(\sigma\tau)=\phi(\sigma)(\sigma\cdot\phi(\tau)),\,\forall\sigma,\,\tau\in G.$$

For any given $\phi$, define the action

$$\sum_{\sigma\in G}\phi(\sigma)\sigma:\,L\to L.$$

Note that since the automorphisms $\sigma$ of $L$ are linearly independent over the coefficient ring $L$ (see [^2], although it's not difficult to verify), this gurantees that the above sum is different than the $0$-map and it is possible to find $\theta\in L$ such that

$$\gamma\overset{\text{def}}{=}\sum_{\sigma\in G}\phi(\sigma)(\sigma\cdot\theta)\neq0.$$

Examining $\sigma\cdot\gamma$ tells us that

$$\begin{align*}\sigma\cdot\gamma &=\sum_{\sigma\in G}(\sigma\cdot\phi(\tau))\sigma\tau\cdot\theta \\  &=\sum_{\tau\in G}(\phi(\sigma))^{-1}\phi(\sigma\tau)(\sigma\tau\cdot\theta) \\  &=(\phi(\sigma))^{-1}\sum_{\tau\in G}\phi(\sigma\tau)(\sigma\tau\cdot\theta) \\  &=(\phi(\sigma))^{-1}\gamma.\end{align*}$$

This implies that $\phi(\sigma)=\gamma/(\sigma\cdot\gamma)$. In the case that $L/K$ is a cyclic extension of degree $n$ we may pick some $\alpha\in L$ such that $N_{L/K}(\alpha)=1$. This lets us define a $1$-cocycle $\alpha:\, G\to L^\times$ (which is really $\alpha\overset{\text{def}}{=}\phi(\sigma)$). But since $H^1(E,\,L^\times)=0$, i.e. the first cohomology group is trivial, this means that any $1$-cocycle is a $1$-coboundary, so there is a $\beta\in L$ such that* $\phi(\sigma)=\beta(\sigma\cdot\beta)^{-1}$. But this is exactly

$$\alpha=\frac{\beta}{\sigma(\beta)}$$

like we wanted!

<sup>2: Here we have switched out our previous additive notation for multiplicitve notation because L<sup>&#215;</sup> is a multiplicative group; addition becomes multiplication and negation corresponds to multiplicative inverses.</sup>

## Parametrizing other integer triangles

It was hinted by Elkies [^4] that the same methodology that we used to parametrize Pythagorean triples may also be employed to describe the solutions of Diophantine equations defined by norms of elements of a quadratic field $\mathbb{Q}(\sqrt{d})$. A natural context to use this in geometry arises when finding all triangles with integer side lengths and an angle equal to $2\pi/3$. We begin by making use of the law of cosines with $\theta=2\pi/3$, this tells us that the side lengths of any such triangle must satisfy

$$X^2+XY+Y^2=Z^2.$$

Setting $X=xZ$ and $Y=yZ$ we get

$$\begin{align*}x^2+xy+z^2&=1,\end{align*}$$

so if we are going to characterize these triangles we should work with a field with norm $x^2+xy+y^2.$ The field we'll need for this is $\mathbb{Q}(\sqrt{-3})$ which has a cyclic Galois group, $\text{Gal}(\mathbb{Q}(\sqrt{-3})/\mathbb{Q})$, with generator

$$\sigma\left(x+y\cdot\frac{1+\sqrt{-3}}{2}\right)=x+y\cdot\frac{1-\sqrt{-3}}{2}.$$

This gives us the norm

$$\begin{align*}N\left( x+y\cdot\frac{1+\sqrt{-3}}{2}\right ) &=\left(x+y\cdot\frac{1+\sqrt{-3}}{2} \right )\sigma\left(x+y\cdot\frac{1+\sqrt{-3}}{2} \right ) \\  &=x^2+xy+y^2, \end{align*}$$

exactly what we wanted. Now we can apply theorem 90 to parametrize all elements $\alpha$ of norm $1$ in $\mathbb{Q}(\sqrt{-3}),$

$$\begin{align*}\alpha &=\frac{\beta}{\sigma(\beta)} \\  &=\left(a+b\cdot\frac{1+\sqrt{-3}}{2} \right )\bigg/\left(a+b\cdot\frac{1-\sqrt{-3}}{2} \right ) \\  &= \frac{a^2-b^2}{a^2+ab+b^2}+\frac{2ab+b^2}{a^2+ab+b^2}\cdot\frac{1+\sqrt{-3}}{2}.\end{align*}$$

Taking the norm of this yields

$$\left(\frac{a^2-b^2}{a^2+ab+b^2}\right)^2+\frac{a^2-b^2}{a^2+ab+b^2}\cdot\frac{2ab+b^2}{a^2+ab+b^2}+\left(\frac{2ab+b^2}{a^2+ab+b^2}\right)^2=1$$

and clearing the denominators tells us that

$$X=a^2-b^2,\,Y=2ab+b^2,\,Z=a^2+ab+b^2.$$

### The case $\theta=\pi/3$

Going through the same motions, we find that the side lengths of a triangle with an angle $\theta=\pi/3$ must satisfy

$$X^2-XY+Y^2=Z^2.$$

Applying theorem 90 shows

$$X=a^2-b^2,\,Y=2ab-b^2,\,Z=a^2-ab+b^2.$$

## Sources

[^1]: *An introduction to group (and Galois) cohomology (part 1)*, Alvaro Lozano-Robledo, [https://www.youtube.com/watch?v=oyhqUFmueLs](https://www.youtube.com/watch?v=oyhqUFmueLs)

[^2]: *Hilbert's Theorem 90*, Seewoo Lee, [https://math.berkeley.edu/~seewoo5/h90.pdf](https://math.berkeley.edu/~seewoo5/h90.pdf)

[^3]: *Beginnings of Group Cohomology*, R. Sridharan, [https://www.ias.ac.in/article/fulltext/reso/010/09/0037-0052](https://www.ias.ac.in/article/fulltext/reso/010/09/0037-0052)

[^4]: *Pythagorean Triples and Hilbert's Theorem 90*, Noam Elkies, [https://abel.math.harvard.edu/~elkies/Misc/hilbert.pdf](https://abel.math.harvard.edu/~elkies/Misc/hilbert.pdf)