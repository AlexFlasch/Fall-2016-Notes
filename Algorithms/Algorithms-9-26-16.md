#Algorithms 9/26/16

##Proving correctness with a loop invariant

```java
long powItr(int b, int n) {
	long product = 1;
	for(int i = 0; i < n; i++) {
		product *= b;
	}
	return product;
}
```

Prove that this algorithm is correct using a loop invariant.

If *product* is equal to $b^n$ at the end of the loop, the algorithm is correct.

Before each iteration, *product* is $b^i$

* Initialization:
	* *product* = 1 = $b^0$
* Maintenance:
	* $product = b^1 \rightarrow product = b^{i+1}$
	* $prodcut = product * b = b^i * b^1 = b^{i+1}$
	* $i++$ 
* Termination:
	* $i = n-1$ 


##Finding a tight asymptotic bound

Give a tight asymptotic bound for lg $N!$

lg $N! = lg(N * (N - 1) ... 2 * 1)$  
$= lg(N) + lg(N -1) + ... + lg(2) + lg(1)$  
$\geq lg(N) + lg(N - 1) + ... + lg(\frac{N}{2})$  
$\geq lg(\frac{N}{2}) + lg(\frac{N}{2}) + ... + lg(\frac{N}{2})$  
$= \frac{N}2{2} lg(\frac{N}{2})$  
$ = \frac{N}{2}(lg(N) - lg(2))$   
$\geq \frac{\frac{N}{2}(lg(N) - \frac{lg(N)}{2})}{2}$  
$= \frac{N}{2} * \frac{lg(N)}{2}$  
$= \frac{N * lg(N)}{4}$  
$= C * N * lg(N)$, for $N \geq N_0$  
$= \Omega (N*log(N)$