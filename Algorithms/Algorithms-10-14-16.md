#Algorithms 10/14/16

##Solving the Average Case of Quicksort

$T(N) = T(q) + T(N-q-1)+c \cdot N$  
Assume all pivot values are equally likely (each pivot value $q$ has a probability of $\frac{1}{N}$)  
Compute the average of $T(q)$ for $q = 0, 1, ..., N-1$  
Average value of $T(q)$ is $(\frac{1}{N}) \sum_{q = 0}^{n}$

$T(N) = (\frac{2}{N}) \sum_{q=0}^n T(q) + c \cdot N$  
We need to turn $T(N)$ into a more convenient form before we can solve it.  
$N \cdot T(N) = 2 \sum_{q=0}^n T(q) + c \cdot N^2$  
$\longleftrightarrow$  
$X$: $N \cdot T(N) = 2(T(0) + T(1) + ... + T(N-1)) + c \cdot N^2$  
$\longleftrightarrow$  
$Y$: $(N-1) \cdot T(N-1) = 2(T(0) + T(1) + ... + T(N-2)) + c \cdot (N^2-2n+1)$

$X - Y$: $(N \cdot T(N)) - ((N-1) \cdot T(N-1)) = (2(T(0) + T(1) + ... + T(N-1)) + c \cdot N^2) - (2(T(0) + T(1) + $  
&nbsp;&nbsp;&nbsp;&nbsp;$... + T(N-2)) + c \cdot (N^2 - 2N + 1))$  
$(N-1) \cdot T(N-1) = 2T(N-1) + c \cdot (2N-1)$  
$N \cdot T(N) = (N-1) \cdot T(N-1) + 2T(N-1) + c \cdot (2N-1)$  
$ = T(N-1) \cdot [N-1+2] + c \cdot (2n-1)$  
$ = (N+1) \cdot T(N-1) + c \cdot (2N-1)$  
$N \cdot T(N) = (N+1) \cdot T(N-1) + c \cdot (2N-1)$  
$\longleftrightarrow$  
$\frac{N \cdot T(N)}{N(N+1)} = \frac{(N+1) \cdot T(N-1) + c \cdot (2N-1)}{N \cdot (N+1)}$  
$\longleftrightarrow$  
$\frac{T(N)}{N+1} = \frac{T(N-1)}{N} + \frac{c \cdot (2N-1)}{N \cdot (N+1)}$  
$E(N) = \frac{c \cdot (2N-1)}{N \cdot (N+1)}$  
$\frac{T(N)}{N+1} = \frac{T(N-1)}{N} + E(N)$  
$\frac{T(N-1)}{N} = \frac{T(N-2)}{N-1} + E(N-1)$  
$\frac{T(N-2)}{N-1} = \frac{T(N-3)}{N-2} + E(N-2)$  
.  
.  
.  
Given: $T(0) = 1$  
$\frac{T(1)}{2} = \frac{T(0)}{1} + E(1)$
Substitute $\frac{T(1)}{2}$ into equation  
$\frac{T(N)}{N+1} = T(0) + E(N) + E(N-1) + ... + E(1)$  
$ = T(0) + \sum_{i=1}^N E(i)$  
$ T(N) = (N+1) + (N+1) \cdot \sum_{i=1}^N E(i)$  
$ = O(N) \cdot \sum_{i=1}^N \frac{c(2i-1)}{i(i+1)}$