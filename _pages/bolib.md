---
layout: archive
title: ""   
permalink: /bolib/
author_profile: true
---

Bilevel optimization has the form

$$ \min_{x,y}~ F(x,y)~~ \mbox{s.t.}~  G(x,y)\leq 0,~ y\in \mbox{argmin}_y~ \{ f(x,y)\mid g(x,y)\leq 0 \}, \nonumber $$

where  $F,f:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}$, $G:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}^{n_G}$ and $g:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}^{n_g}$. We say  above problem is linear if all its involved functions $F, G, f$ and $g$ are linear, otherwise, it is nonlinear. Simple bilevel optimization is defined by

$$ \min_{x,y}~ F(y)~~ \mbox{s.t.}~  G(y)\leq 0,~ y\in \mbox{argmin}_y~ \{ f(y)\mid g(y)\leq 0 \}. \nonumber $$


$\texttt{BOLIB}$
---

 This is the old version of  bilevel optimization test problems libary: $\texttt{BOLIB}$ ([more information here](https://github.com/ShenglongZhou/BOLIB)).  It only contains 124 nonlinear bilevel optimization test examples ([more details here](https://www.researchgate.net/publication/325120369)). All examples are coded through Matlab and saved in m-files. Each m-file has similar pattern.

$\texttt{BOLIBver2}$
---
This is a new version constructed based on the old one. [BOLIBver2.zip](\files\BOLIBEver2.zip) comprises  138 nonlinear including 124 ones from $\texttt{BOLIB}$, 24 linear and  11 simple bilevel optimization test examples. Refer to [BOLIB2019_test_examples_library_version2.pdf](\files\BOLIB2019_test_examples_library_version2.pdf) for more information, such as dimensions, best known solutions  or  starting points. 
