---
title: A Hyperbolic PDE
# author: dxdydz
date: 2023-07-19 15:25:00 -0400
categories: [Calculus]
tags: [PDEs, differential equations, python]
math: True
pin: False
---

Several months ago I saw [this image](https://i.imgur.com/afTMvuj.jpg) and wondered if the plot shown in the original probelm was actually the solution to the stated PDE. In addition to being a fun problem it's also a good excuse to play with some plots in python.

## Problem

Solve

$$\begin{align}    \left(\frac{\partial^2}{\partial x^2}+3\frac{\partial^2}{\partial x\partial y}-4\frac{\partial^2}{\partial y^2}\right)f(x,\,y)=xy\tag{1}\end{align}$$

subject to the conditions

$$f(x,\,x)=\sin(x)$$

and

$$\frac{\partial}{\partial x}f(x,\,y)\bigg\vert_{y=x}=0.$$

## Solution

First we note this is a hyperbolic partial differential equation with

$$\lambda_1=1,\,\lambda_2=-\frac{1}{4}.$$

In order to find a solution we start by making a change of variables $u=x+\lambda_1y$ and $v=x+\lambda_2y$. Let $h(u,\,v)=f(x+\lambda_1y,\,x+\lambda_2y)$, differentiating then gives the equations

$$\frac{\partial^2}{\partial x^2}f(x,\,y)=\left(\frac{\partial^2}{\partial u^2}+2\frac{\partial^2}{\partial u\partial v}+\frac{\partial^2}{\partial v^2}\right)h(u,\,v),$$

$$\frac{\partial^2}{\partial x\partial y}f(x,\,y)=\left(\frac{\partial^2}{\partial u^2}+\frac{3}{4}\frac{\partial^2}{\partial u\partial v}-\frac{1}{4}\frac{\partial^2}{\partial v^2}\right)h(u,\,v),$$

$$\frac{\partial^2}{\partial y^2}f(x,\,y)=\left(\frac{\partial^2}{\partial u^2}-\frac{1}{2}\frac{\partial^2}{\partial u\partial v}+\frac{1}{16}\frac{\partial^2}{\partial v^2}\right)h(u,\,v).$$

Substituting these into $(1)$ (and noting that $x=4(v+u/4)/5,\,y=4(u-v)/5$) causes something nice to happen; the original PDE reduces to

$$\frac{\partial^2}{\partial u\partial v}h(u,\,v)=\frac{16}{625}\left(u^2+3uv-4v^2\right).$$

Now we may integrate this to get

$$\begin{align}    h(u,\,v)=\frac{16}{625}\left(\frac{u^3v}{3}+\frac{3u^2v^2}{4}-\frac{4uv^3}{3}\right)+s(u)+t(v).\tag{2}\end{align}$$

Both of the initial conditions give

$$\frac{41x^4}{625}+s(2x)+t(3x/4)=\sin(x)$$

and

$$\frac{326x^3}{1875}+s'(2x)+t'(3x/4)=0.$$

Integrating this second equation results in

$$\frac{163x^4}{1250}+\frac{s(2x)}{2}+\frac{4t(3x/4)}{3}=C.$$

We may then solve for $s(2x)$ and $t(3x/4)$,

$$s(2x)=\frac{161x^4}{3125}-\frac{6C}{5}+\frac{8\sin(x)}{5}$$

and

$$t(3x/4)=-\frac{366x^4}{3125}+\frac{6C}{5}-\frac{3\sin(x)}{5}.$$

Substituting these into $(2)$ and changing back to $x,\,y$ yields

$$f(x,\,y) = -\frac{100801x^4}{270000}+\frac{28807x^3y}{67500}-\frac{719x^2y^2}{9000}+\frac{371y^4}{270000}-\frac{3}{5}\sin\left(\frac{4x-y}{3}\right)+\frac{8}{5}\sin\left(\frac{x+y}{2}\right).$$

So, back to the initial question, does this function look like the plot in the original image?

```python
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

def f(x, y):
    return (-100801*x**4)/270000+(28807*(x**3)*y)/67500-(719*(x**2)*y**2)/9000+(371*y**4)/270000-(3/5)*np.sin((4*x-y)/3)+(8/5)*np.sin((x+y)/2)

x = np.linspace(-100, 100, 1000)
y = np.linspace(-100, 100, 1000)
X, Y = np.meshgrid(x, y)

fig = plt.figure()
ax = fig.add_subplot(111, projection='3d')
ax.plot_surface(X, Y, f(X,Y), cmap='viridis')

ax.set_title("$f(x,\,y)$")
ax.set_xlabel('X')
ax.set_ylabel('Y')
ax.set_zlabel('Z')

plt.show()
```

After some generous toying with the scaling of the axes, I say no.

<center><a href="https://imgur.com/a/Y2hgEkJ"><img src="https://i.imgur.com/hA35Kp4.png" alt="centered image" height="auto" width="400" title="source: imgur.com" /></a></center>