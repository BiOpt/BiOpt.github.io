---
layout: archive
title: ""   
permalink: /bolib/
author_profile: true
---

Bilevel optimization has the form

$$ \min_{x,y}~ F(x,y)~~ \mbox{s.t.}~  G(x,y)\leq 0,~ y\in \mbox{argmin}_y~ \{ f(x,y)\mid g(x,y)\leq 0 \}, \nonumber $$

where  $F,f:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}$, $G:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}^{n_G}$ and $g:\mathbb{R}^{n_x}\times\mathbb{R}^{n_y}\rightarrow \mathbb{R}^{n_g}$. We say  above problem is linear if all its involved functions $F, G, f$ and $g$ are linear, otherwise, it is nonlinear. Simple bilevel optimization is defined by

$$ \min_{y}~ F(y)~~ \mbox{s.t.}~  G(y)\leq 0,~ y\in \mbox{argmin}_y~ \{ f(y)\mid g(y)\leq 0 \}. \nonumber $$


$\texttt{BOLIB}$
---

 This is the old version of  bilevel optimization test problems libary: $\texttt{BOLIB}$ ([more information here](https://github.com/ShenglongZhou/BOLIB)).  It only contains 124 nonlinear bilevel optimization test examples ([more details here](https://www.researchgate.net/publication/325120369)). All examples are coded through Matlab and saved in m-files. Each m-file has similar pattern. For example,
 
 ```
function w=DempeLohse2011Ex31b(x,y,keyf,keyxy)

if nargin<4 || isempty(keyxy)
    switch keyf
    case 'F'; w = sum((x-[.5; .5; 0]).^2)-[3 3 6]*y;
    case 'G'; w = [];      
    case 'f'; w = sum(x.*y);     
    case 'g'; w = [1 1 1; -1 1 0; -eye(3)]*y-[2;0;0;0;0];
    end    
else
    switch keyf
    case 'F'
        switch keyxy
        case 'x' ; w = 2*x-[1 1 0]';        
        case 'y' ; w = [-3;-3;-6];       
        case 'xx'; w = 2*eye(3);
        case 'xy'; w = zeros(3);
        case 'yy'; w = zeros(3);
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
        case 'x' ; w = y;    
        case 'y' ; w = x;         
        case 'xx'; w = zeros(3);
        case 'xy'; w = eye(3);
        case 'yy'; w = zeros(3);
        end           
	case 'g'    
        switch keyxy
        case 'x' ; w = zeros(5,3);
        case 'y' ; w = [ 1 1 1; -1 1 0; -eye(3)];             
        case 'xx'; w = zeros(15,3);
        case 'xy'; w = zeros(15,3);
        case 'yy'; w = zeros(15,3);
        end        
   end   
end

end

 ```

$\texttt{BOLIBver2}$
---
This is a new version constructed based on the old one. [BOLIBver2.zip](\files\BOLIBEver2.zip) comprises  138 nonlinear including 124 ones from $\texttt{BOLIB}$, 24 linear and  11 simple bilevel optimization test examples. Refer to [BOLIB2019_test_examples_library_version2.pdf](\files\BOLIB2019_test_examples_library_version2.pdf) for more information, such as dimensions, best known solutions  or  starting points. 
