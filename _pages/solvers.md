---
layout: archive
title: ""   
permalink: /solvers/
author_profile: true
---

Bilevel optimization has the form

$$ \min_{x,y}~ F(x,y)~~ \mbox{s.t.}~  G(x,y)\leq 0,~ y\in \mbox{argmin}_y~ \{ f(x,y)\mid g(x,y)\leq 0 \}, \nonumber $$

where  $F,f:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}$, $G:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}^{n_G}$ and $g:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}^{n_g}$.

$\texttt{SNLLVF}$
---
This approach is to transform the bilevel program into a single-level optimization problem by using
the lower-level value function (LLVF) reformulation, namely,  $ f(x,y) = \varphi(x) := \underset{z}\min$ \{ $ f(x,z) \mid g(x,z)\leq 0 $ \}.   By doing so, $\texttt{SNLLVF}$ aims at solving a partial penalization

$$ \underset{x,y}\min~ F(x,y) + \lambda (f(x,y) -\varphi(x)) ~~ \mbox{ s.t. }~  G(x,y)\leq 0,~ g(x,y)\leq 0. \nonumber $$
 
 
$\texttt{SNQVI}$
---
This approach is to transform the bilevel program into a single-level optimization problem 
by converting the lower-level problem to its variational inequalities conditions, a stationary condition: $ \langle \nabla_y f(x,y), z-y \rangle \geq0, \forall~z: g(x,z)\leq 0$ for any $y: g(x,y)\leq 0$. Let $\varphi(x,y) := \underset{z}\min$ \{ $\nabla_y f(x,y)^\top z \mid g(x,z)\leq 0 $ \} .  By doing so,  $\texttt{SNQVI}$ aims at solving a partial penalization

$$ \underset{x,y}\min~ F(x,y)+ \lambda ( \nabla_y f(x,y)^\top z-\varphi(x,y) ) \;\mbox{ s.t. } \; G(x,y)\leq 0,  \ \   g(x,y)\leq 0. \nonumber $$


$\texttt{SNKKT}$
---
This approach is to transform the bilevel program into a single-level optimization problem 
by converting the lower-level problem to its KKT conditions: $ \nabla_y f(x,y)-\nabla_y g(x,y)^\top z=0,~ g(x,y)\leq 0,~  z \leq 0,~   g(x,y)^\top z=0. $ By doing so,  \texttt{SNKKT} aims at solving a partial penalization

$$ \underset{x,y,z}\min~ F(x,y)+ \lambda g(x,y)^\top z \;\mbox{ s.t. } \; G(x,y)\leq 0,  \ \   g(x,y)\leq 0
\ \ z \leq 0,\ \ \nabla_y f(x,y)-\nabla_y g(x,y)^\top z=0. \nonumber $$


