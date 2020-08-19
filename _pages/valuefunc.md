---
layout: archive
title: ""   
permalink: /valuefunc/
author_profile: true
---

<span style="color:grey">Optimal-value function tools</span> 
===

This toolbox <span style="color:blue">**OptValFunc**</span> aim at operating an optimal-value function in the form 

$$ \psi(x) = \min_{y} \{f(x, y):~g(x; y)\leq 0\},\nonumber $$

where $x\in\mathbb{R}^{n_x},y\in\mathbb{R}^{n_y}$ and $g:\mathbb{R}^{n_x\times n_y}\rightarrow \mathbb{R}^{n_g}$. Detailed instructions of this toolbox can be found in the [menu-of-BiOpt.pdf](\files\menu-of-BiOpt.pdf). <span style="color:blue">**OptValFunc**</span> ([OptValFunc.zip](\files\OptValFunc.zip)) provides two tools:

<span style="color:grey">SolOVF</span> 
---
It solves the above minimization problem with providing the function values and corresponding optimal solutions.
 
<span style="color:grey">PlotOVF</span> 
---
It plots the graph of $\psi(x)$ along with $x$. Thus for the purpose of visualization, the dimension $n_x$ of $x$ must be 1 (for two dimensional space) or 2 (for three dimensional space). For example，

<center><img src="/images/ovf111.png" ></center>
<center><img src="/images/ovf222.png" ></center>
