---
layout: archive
title: ""   
permalink: /bolib/
author_profile: true
---

<span style="color:grey">Bilevel optimization library of test problems</span> 
===
This library tidies up  173 bilevel optimization test examples containing 24 linear, 138 nonlinear and  11 simple ones from a wide range of pablications. A [bilevel optimization problem](https://biopt.github.io/solvers/) is linear if all its involved functions $F, G, f$ and $g$ are linear, otherwise, it is nonlinear. As a special class of bilevel optimization,  simple bilevel optimization is defined by

$$ \min_{y}~ F(y)~~ \mbox{s.t.}~  G(y)\leq 0,~ y\in \mbox{argmin}_y~ \{ f(y)\mid g(y)\leq 0 \}. \nonumber $$

<span style="color:grey">BOLIB</span>
---

 This is the old version of  bilevel optimization test problems library: <span style="color:blue">**BOLIB**</span> ([more information here](https://github.com/ShenglongZhou/BOLIB)).  It contains 124 nonlinear bilevel optimization test examples ([more details here](https://www.researchgate.net/publication/325120369)). 

<span style="color:grey">BOLIBver2</span>
---
This is a new version constructed based on the old one. [BOLIBver2.zip](\files\BOLIBver2.zip) comprises 173  bilevel optimization test examples: 138 nonlinear  (in which 124 ones are taken from <span style="color:blue">**BOLIB**</span>), 24 linear and  11 simple ones. The whole list can be found in [BOLIB 2019: Bilevel Optimization LIBrary of test problems version 2.pdf](\files\Paper.pdf). All examples are coded through Matlab and saved in m-files. Each m-file has similar pattern. For example,
 
 ```
function w=Outrata1990Ex1a(x,y,keyf,keyxy)
% This file provides all functions defining Outrata1990Ex1a problem and their first and second order derivatives.
% [dim_x dim_y dim_G dim_g] = [2 2 0 4]

if nargin<4 || isempty(keyxy)
    switch keyf
    case 'F'; w = 0.1*(x'*x)+0.5*sum((y-[3; 4]).^2)-12.5;
    case 'G'; w = [];   
    case 'f'; w = 0.5*(y'*[1 -2; -2 5]*y)-x'*y;
    case 'g'; w = [[-0.333 1]*y-2; [1 -0.333]*y-2; -y];   
    end    
else
    switch keyf
    case 'F'
        switch keyxy
        case 'x' ; w = 0.2*x;         
        case 'y' ; w = y -[3; 4];     
        case 'xx'; w = 0.2*eye(2);
        case 'xy'; w = zeros(2);
        case 'yy'; w = eye(2);
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
        case 'x' ; w = -y;    
        case 'y' ; w = [1 -2; -2 5]*y-x;        
        case 'xx'; w = zeros(2);
        case 'xy'; w = -eye(2);
        case 'yy'; w = [1 -2; -2 5];
        end           
    case 'g'   
        switch keyxy
        case 'x' ; w = zeros(4,2);
        case 'y' ; w = [-0.333 1; 1 -0.333; -eye(2)];                
        case 'xx'; w = zeros(8,2);
        case 'xy'; w = zeros(8,2);
        case 'yy'; w = zeros(8,2);
        end        
   end   
end
end
 ```
This m-file defines one example from [Outrata](https://link.springer.com/article/10.1007/BF01416737), including all function values, first and second- order derivatives of $F, G, f$ and $g$.
