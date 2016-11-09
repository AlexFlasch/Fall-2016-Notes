#Algorithms 10/17/16

##Average cases

$S(N) = \sum\limits_{i=1}^{N} \frac{2i-1}{i(i+1)} < \sum\limits_{i=1}^{N} \frac{2i}{i(i+1)}$

$ = 2 \sum\limits_{i=1}^{N} \frac{i}{i(i+1)}$ cross out $i$

$ = 2 \sum\limits_{i=1}^{N} \frac{1}{i+1}$

$ < 2 \sum\limits_{i=i}^{N} \frac{1}{i}$

now, prove $\sum\limits_{i=1}^{N} \frac{1}{i} = O(logN)$