---
layout: archive
title: ""   
permalink: /solvers/
author_profile: true
---

<span style="color:orange">Bilevel optimization solvers</span> 
===

Bilevel optimization has the form

\begin{eqnarray}\min_{x,y} &&   F(x,y) \nonumber\\\\\\
\mbox{s.t.} && G(x,y)\leq 0,~ y\in \mbox{argmin}_y~ \lbrace f(x,y)\mid g(x,y)\leq 0\rbrace, \nonumber
\end{eqnarray}

 
where  $F,f:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}$, $G:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}^{n_G}$ and $g:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}^{n_g}$. It only takes inequalities constraints into consideration. This two level optimization can be transformed into a single-level version so that Semi-smooth Newton type method is able to be used. 

<span style="color:orange">SNLLVF</span>
---
This approach is to transform the bilevel program into a single-level optimization problem by using
the lower-level value function (LLVF) reformulation, namely,  $g(x,y)\leq 0, f(x,y) = \varphi(x) := \underset{z}\min\lbrace f(x,z) \mid g(x,z)\leq 0 \lbrace$.   By doing so, <span style="color:blue">**SNLLVF**</span> aims at solving a partial penalization

\begin{eqnarray}\min_{x,y} && F(x,y) + \lambda (f(x,y) -\varphi(x)) \nonumber\\\nonumber\\\nonumber\\
\mbox{ s.t. } &&  G(x,y)\leq 0,~ g(x,y)\leq 0. \nonumber
\end{eqnarray}
 
<span style="color:orange">SNQVI</span>
---
This approach is to transform the bilevel program into a single-level optimization problem 
by converting the lower-level problem to its quasi-variational inequality conditions, a stationary condition: $ \langle \nabla_y f(x,y), z-y \rangle \geq0, \forall~z: g(x,z)\leq 0$ for any $y: g(x,y)\leq 0$. Let $\varphi(x,y) := \underset{z}\min$ \{ $\nabla_y f(x,y)^\top z \mid g(x,z)\leq 0 $ \} .  By doing so,  <span style="color:blue">**SNQVI**</span> aims at solving a partial penalization

\begin{eqnarray}\min_{x,y} && F(x,y)+ \lambda ( \nabla_y f(x,y)^\top y-\varphi(x,y) ) \nonumber\\\\\\
\mbox{ s.t. } && G(x,y)\leq 0,  \ \   g(x,y)\leq 0. \nonumber
\end{eqnarray}


<span style="color:orange">SNKKT</span>
---
This approach is to transform the bilevel program into a single-level optimization problem 
by converting the lower-level problem to its KKT conditions: $ \nabla_y f(x,y)-\nabla_y g(x,y)^\top z=0,~ g(x,y)\leq 0,~  z \leq 0,~   g(x,y)^\top z=0. $ By doing so,  <span style="color:blue">**SNKKT**</span> aims at solving a partial penalization

\begin{eqnarray}
\min_{x,y,z}  && F(x,y)+ \lambda g(x,y)^\top z\nonumber\\\\\\
\mbox{ s.t. } && G(x,y)\leq 0,  \   g(x,y)\leq 0,\ z \leq 0, \ \nabla_y f(x,y)-\nabla_y g(x,y)^\top z=0. \nonumber
\end{eqnarray}  


<span style="color:orange">BiOpt-Solvers</span>
---
[BiOpt-Solvers.zip](/files/BiOpt-Solvers.zip) provides three solvers: <span style="color:blue">**SNLLVF**</span>, <span style="color:blue">**SNQVI**</span>  and <span style="color:blue">**SNKKT**</span> based on above three reformulations. Detailed descriptions of using them can be found in  the [menu-of-BiOpt.pdf](\files\menu-of-BiOpt.pdf). Here we give a simple example to illustrate it:

```
clc; clear; close all; 

ExName     = 'DempeDutta2012Ex24'; 
func       = str2func(ExName);
dim        = [1 1 0 1];     % required
pars.xy    = [1;1];         % optional

pars.lam   = 1;             % optional
pars.keep  = 0;             % optional 
pars.check = 1;             % optional

SolNo      = 1;     % choose the solve
Solvers    = {'SNLLVF','SNQVI','SNKKT'}; 
solver     = str2func(Solvers{SolNo});  
Out1       = solver(func, dim,  pars);
```

Each solver have two required inputs: 'func' defining the example and 'dim' recording dimensions of the example, and an optinal input 'pars' including some parameters. Please see the [menu-of-BiOpt.pdf](\files\menu-of-BiOpt.pdf) for more details of 'pars'. The chosen solver is <span style="color:blue">**SNLLVF**</span> and the solved example is 'DempeDutta2012Ex24' defined by following Matlab m-file:

```
function w=DempeDutta2012Ex24(x,y,keyf,keyxy)
% This file provides all functions defining DempeDutta2012Ex24 problem and their first and second order derivatives.
% [dim_x dim_y dim_G dim_g] = [1 1 0 1]
if nargin<4 || isempty(keyxy)
    switch keyf
    case 'F'; w = (x-1)^2+y^2;
    case 'G'; w = []; 
    case 'f'; w = x^2*y;      
    case 'g'; w = y^2; 
    end    
else
    switch keyf
    case 'F'
        switch keyxy
        case 'x' ; w = 2*(x-1);         
        case 'y' ; w = 2*y;        
        case 'xx'; w = 2;
        case 'xy'; w = 0;
        case 'yy'; w = 2;
        end 
    case 'G'  
        switch keyxy
        case 'x' ; w = [];    
        case 'y' ; w = [];      
        case 'xx'; w = [];
        case 'xy'; w = [];
        case 'yy'; w = [];
        end           
	case 'f'   
        switch keyxy
        case 'x' ; w = 2*x*y;    
        case 'y' ; w = x^2;          
        case 'xx'; w = 2*y;
        case 'xy'; w = 2*x;
        case 'yy'; w = 0;
        end           
	case 'g'   
        switch keyxy
        case 'x' ; w =   0;  
        case 'y' ; w =   2*y;         
        case 'xx'; w =   0;  
        case 'xy'; w =   0;  
        case 'yy'; w =   2; 
        end        
   end   
end
end
```

This example is from <span style="color:blue">**BOLIBver2**</span> ([BOLIBver2.zip](/files/BOLIBver2.zip)), in which more examples can be found. In  the [menu-of-BiOpt.pdf](\files\menu-of-BiOpt.pdf), we also present several other ways to define the examples that are different with the way to define examples in  <span style="color:blue">**BOLIBver2**</span> .
