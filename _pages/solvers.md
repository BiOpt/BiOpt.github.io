---
layout: archive
title: ""   
permalink: /solvers/
author_profile: true
---

Bilevel optimization has the form

$$ \min_{x,y}~ F(x,y)~~ \mbox{s.t.}~  G(x,y)\leq 0,~ y\in \mbox{argmin}_y~ \{ f(x,y)\mid g(x,y)\leq 0 \}, \nonumber $$

where  $F,f:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}$, $G:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}^{n_G}$ and $g:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}^{n_g}$. This two level optimization can be transformed into a single-level version so that Semi-smooth Newton type method is able to be used. 

$\texttt{SNLLVF}$
---
This approach is to transform the bilevel program into a single-level optimization problem by using
the lower-level value function (LLVF) reformulation, namely,  $g(x,y)\leq 0, f(x,y) = \varphi(x) := \underset{z}\min$ \{ $ f(x,z) \mid g(x,z)\leq 0 $ \}.   By doing so, $\texttt{SNLLVF}$ aims at solving a partial penalization

$$ \underset{x,y}\min~ F(x,y) + \lambda (f(x,y) -\varphi(x)) ~~ \mbox{ s.t. }~  G(x,y)\leq 0,~ g(x,y)\leq 0. \nonumber $$
 
 
$\texttt{SNQVI}$
---
This approach is to transform the bilevel program into a single-level optimization problem 
by converting the lower-level problem to its variational inequalities conditions, a stationary condition: $ \langle \nabla_y f(x,y), z-y \rangle \geq0, \forall~z: g(x,z)\leq 0$ for any $y: g(x,y)\leq 0$. Let $\varphi(x,y) := \underset{z}\min$ \{ $\nabla_y f(x,y)^\top z \mid g(x,z)\leq 0 $ \} .  By doing so,  $\texttt{SNQVI}$ aims at solving a partial penalization

$$ \underset{x,y}\min~ F(x,y)+ \lambda ( \nabla_y f(x,y)^\top y-\varphi(x,y) ) \;\mbox{ s.t. } \; G(x,y)\leq 0,  \ \   g(x,y)\leq 0. \nonumber $$


$\texttt{SNKKT}$
---
This approach is to transform the bilevel program into a single-level optimization problem 
by converting the lower-level problem to its KKT conditions: $ \nabla_y f(x,y)-\nabla_y g(x,y)^\top z=0,~ g(x,y)\leq 0,~  z \leq 0,~   g(x,y)^\top z=0. $ By doing so,  $\texttt{SNKKT}$ aims at solving a partial penalization

$$ \underset{x,y,z}\min~ F(x,y)+ \lambda g(x,y)^\top z \;\mbox{ s.t. } \; G(x,y)\leq 0,  \ \   g(x,y)\leq 0
\ \ z \leq 0,\ \ \nabla_y f(x,y)-\nabla_y g(x,y)^\top z=0. \nonumber $$


$\texttt{BiOpt-Solvers}$ 
---
[BiOpt-Solvers.zip](/files/BiOpt-Solvers.zip) provides three solvers: $\texttt{SNLLVF}$, $\texttt{SNQVI}$ and $\texttt{SNKKT}$ based on above three reformulations. Detailed descriptions of using them can be found in  the [menu-of-BiOpt.pdf](\files\menu-of-BiOpt.pdf). Here we give a simple example to illustrate them.

```
clc; clear; close all; 

ExName     = 'DempeDutta2012Ex24_ver1'; 
func       = str2func(ExName);
dim        = [1 1 0 1];
pars.xy    = [1;1];

pars.lam   = 1;
pars.keep  = 0; 
pars.check = 1; 

SolNo      = 1;     % choose the solver
Solvers    = {'SNLLVF','SNQVI','SNKKT'}; 
solver     = str2func(Solvers{SolNo});  
Out1       = solver(func, dim,  pars);
```

Here the solved example is 'DempeDutta2012Ex24_ver1' which is defined by a Matlab m-file as

```
function w=DempeDutta2012Ex24_ver1(x,y,keyf,keyxy)
% [dim_x dim_y dim_G dim_g] = [1 1 0 1]
if nargin<4 || isempty(keyxy)
    switch keyf
    case 'F'; w = (x-1)^2+y^2;
    case 'G'; w = []; 
    case 'f'; w = x^2*y;      
    case 'g'; w = y^2; 
    end    
end
end
```
