---
layout: archive
title: ""   
permalink: /valuefunc/
author_profile: true
---

<span style="color:grey">Optimal-value function tools</span> 
===
<div style="text-align:justify;"> 
This toolbox <a href="\files\OptValFunc.zip">OptValFunc</a> aims at operating an optimal-value function in the form 
</div> 
$$ \psi(x) = \min_{y} \{f(x, y):~g(x; y)\leq 0\},\nonumber $$
<div style="text-align:justify;"> 
where $x\in\mathbb{R}^{n_x},y\in\mathbb{R}^{n_y}$ and $g:\mathbb{R}^{n_x\times n_y}\rightarrow \mathbb{R}^{n_g}$. Detailed instructions of this toolbox can be found in the  <a href="\files\menu-of-BiOpt.pdf">menu-of-BiOpt</a>. <a href="\files\OptValFunc.zip">OptValFunc</a> provides two tools:
</div> 

<span style="color:grey">SolOVF</span> 
---
<div style="text-align:justify;"> 
It solves the above minimization problem with providing the function values and corresponding optimal solutions.
 </div> 
 
<span style="color:grey">PlotOVF</span> 
---
<div style="text-align:justify;"> 
It plots the graph of $\psi(x)$ along with $x$. Thus for the purpose of visualization, the dimension $n_x$ of $x$ must be 1 (for two dimensional space) or 2 (for three dimensional space). For example，
</div> 
<center><img src="/images/ovf111.png" ></center>
<center><img src="/images/ovf222.png" ></center>
