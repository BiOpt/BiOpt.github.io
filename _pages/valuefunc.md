---
layout: archive
title: ""   
permalink: /valuefunc/
author_profile: true
---

This toolbox $\texttt{OptValFunc}$ aims to operate an optimal-value function (OVF) in the form 

$$~~~~~~~~~~~ \psi(x) = \min_{y} \{f(x, y):~g(x; y)\leq 0\},\nonumber $$

where $x\in\mathbb{R}^{n_x},y\in\mathbb{R}^{n_y}$ and $g:\mathbb{R}^{n_x\times n_y}\rightarrow \mathbb{R}^{n_g}$. Detailed descriptions of usage of this toolbox can be found in  the [menu-of-BiOpt.pdf](\files\menu-of-BiOpt.pdf). Download the file [OptValFunc.zip](\files\OptValFunc.zip) in which there are two tools:

$\texttt{SolOVF}$
---
It solves the above minimization problem with providing the function values and corresponding optimal solutions.
 
$\texttt{PlotOVF}$
---
It plots the graph of $\psi(x)$ along with $x$. Thus for the purpose of visualization, the dimension $n_x$ of $x$ must be 1 (for two dimensional space) or 2 (for three dimensional space). For example


![svf-1](/images/ovf11.png) 

![svf-3](/images/ovf22.png)  

 
 
