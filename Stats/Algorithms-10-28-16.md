#Algorithms 10/28/16

##Aggregate Analysis of Binary Counter Assembly

Assume $N = 2^k + 1$  
After $N$ rows, we have $k + 1$ columns of bits in the counter  
Leb $b_i =$ number of times bit in column $i$ is incremented (from 0 to 1, or 1 to 0)  
&nbsp;&nbsp;&nbsp;&nbsp;(LSB is bit 0)  
T(N) = ???  
$\frac{T(N)}{N} = O(???)$  

Counting all tiles that are incremented:  
$b_0 + b_1 + ... + b_k$  
$T(N) = \{b_0 = 2^k, b_1 = 2^{k-1}, b_2 = 2^{k-2}, ... , b_k = 1\} = \sum\limits_{i=0}^k 2^i = 2^{k+1}$  
$\frac{T(N)}{N} = \frac{2^{k+1} - 1}{N} = \frac{2^{O(log N)} - 1}{N} \leq \frac{2^{O(log N)}}{N} = \frac{O(N)}{N} = O(1)$  
$k = O(log N)$


##Potential Function Analysis of MyArray

$\Phi(D_i) = 2e_i - N_i \longleftarrow$ length of array after operation $i$  
$2e_i \longleftarrow$ # of elements in MyArray after operation $i$.

$(i = 2^k)$ $ --- \hat{c}_i = c_i + \Phi(D_i) - \Phi(D_{i-1})$  
$ = 1 + e_{i-1} + (2e_i - N_i) - (2e_{i-1} - N_{i-1}) \longleftarrow e_i = e_{i-1} + 1, N_i = 2 \cdot N_{i-1} = 2e_i$  
$ = 1 + e_{i-1} + (2(e_{i-1}+1) - 2e_{i-1}) - (2e_{i-1} - e_{i-1})$  
$ = 1 + e_{i-1} + (2e_{i-1} + 2 - 2e_{i-1}) - e_{i-1}$  
$ = 3$  
testing potential function   
$ = 1 + (2e_i - N_i) - (2e_{i-1} - N_{i-1})$  
$ = 1 + (2(e_{i-1} + 1) - N_{i-1}) - (2e_{i-1} - N_{i-1})$  
$ = 1 + 2e_{i-1} + 2 - N_{i-1} - 2e_{i-1} + N_{i-1}$  
cancel $2e_{i-1}$ and $N_{i-1}$  
$ = 3$


##Greedy Algorithms

###Making Change

We have the following coins: dollars, quarters, dimes, nickels, and pennies. We will describe an algorithm for paying a given amount to a customer. Use the smallest number of coins.

Example $2.89

2 dollars, 3 quarters, 1 dime, and 4 pennies