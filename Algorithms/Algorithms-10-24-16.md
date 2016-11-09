#Algorithms 10/21/16

##Amortized analysis of the "Quack"

$\hat{c}_i = c_i + (\Phi(D_i) - \Phi(D_{i-1})$  
$\Phi(D_i) = L + R$  

**Add:**  
$\hat{c}_i = 1 + ((L + 1 + R) - (L + R))$  
&nbsp;&nbsp;&nbsp;&nbsp; $ = 1 + L + 1 + R - L - R$  
&nbsp;&nbsp;&nbsp;&nbsp; $ = 2$

**Remove:**  
Case 1, R empty:  
$\hat{c}_i = c_i + \Phi(D_i) - \Phi(D_{i - 1})$  
&nbsp;&nbsp;&nbsp;&nbsp; $ = L + ((L - 1) - (L + 0))$
&nbsp;&nbsp;&nbsp;&nbsp; $ = L - 1$  
&nbsp;&nbsp;&nbsp;&nbsp; $ = \Theta(N) \longleftarrow$ bad, need a new potential function

Case 2, R not empty:  
$\hat{c}_i = c_i + \Phi(D_i) - \Phi(D_{i - 1}$  
&nbsp;&nbsp;&nbsp;&nbsp; $ = 1 + ((R - 1 + L) - (R + L))$  
&nbsp;&nbsp;&nbsp;&nbsp; $ = 1 + R - 1 + L - R  - L$  
&nbsp;&nbsp;&nbsp;&nbsp; $ = 0$


##Self-assembly

**self-assembly** is unorganized, simple components automatically combine to form something interesting.

We'll be using an abstract tile assembly model (aTAM)

Each side has strength, represented by the number of notches on that side, and tag represented by the color of the notch.