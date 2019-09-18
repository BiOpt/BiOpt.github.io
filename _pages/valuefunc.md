---
layout: archive
title: ""   
permalink: /valuefunc/
author_profile: true
---

This toolbox [OptValFunc](\files\OptValFunc.zip) aims to operate an optimal-value function (OVF) in the form 

$$~~~~~~~~~~~~~~~~ \psi(x) = \min_{y} \{f(x, y):~g(x; y)\leq 0\}$$.

where $x\in\mathbb{R}^{n_x},y\in\mathbb{R}^{n_y}$ and $g:\mathbb{R}^{n_x\times n_y}\rightarrow \mathbb{R}^{n_g}$. This toolbox comrises two tools: \texttt{SolOVF} and \texttt{PlotOVF}.


\texttt{SolOVF}
---
solves the above minimization problem with providing the function values and corresponding optimal solutions.
 
\texttt{PlotOVF}
---
plots  the graph $\psi(x)$ along with $x$. 
