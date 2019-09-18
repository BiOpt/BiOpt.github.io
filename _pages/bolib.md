---
layout: archive
title: ""   
permalink: /bolib/
author_profile: true
---

This bilevel optimization test problems libary is constructed from the old version of $\texttt{BOLIB}$
([more information here](https://github.com/ShenglongZhou/BOLIB) ). 
The old version contains 124 nonlinear bilevel optimization test
examples ([more details here](https://www.researchgate.net/publication/325120369) ). 

This new version of $\texttt{BOLIBver2}$ can be [downloaded here](\files\BOLIBExamples.zip), which comprises  138 nonlinear, 24 linear and  11 Simple bilevel optimization test examples. One can refer [BOLIB2019_test_examples_library_version2](\files\BOLIB2019_test_examples_library_version2.pdf) for more detailed information, such as the dimensions, best known optimal upper and lower-level objective function
values, or the starting points. All examples are coded through Matlab and saved in m-files. Here the coded  bilevel optimization has the form

\begin{equation}\label{P}
   \underset{x,y}\min~ F(x,y)~~ \mbox{s.t.}~  G(x,y)\leq 0,~ y\in \underset{y}\mbox{argmin}~ \{ f(x,y)\mid g(x,z)\leq 0 \}
\end{equation}
where  $F,f:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}$, $G:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}^{n_G}$ and $g:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}^{n_g}$.
