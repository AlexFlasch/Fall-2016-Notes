#Algorithms 9/12/16

##Homework 1

### 6) Base case

$h(T) = n(L) + n$($R$)$ + 1$


##Back to the maximum subsquence problem

###Recursive Divide and Conquer

Base case: $T(1) = 1$  
$T(N) = T(\frac{N}{2}) + T(\frac{N}{2}) + \theta(N)$  
$T(N) = 2T(\frac{N}{2}) + \theta(N)$


###Solving the runtime of the recursive d&c algorithm

Let $k = 4$  
Assume that $N = 2^k (= 2^4)$  
$T(N) = T(2^4) = 2T(2^3) + c * 2^4$  
$ = 2(2T(2^2) + c * 2^3) + c * 2^4$  
$ = 2(2(2T(2) + c * 2^2) + c * 2^3) + c * 2^4)$  
$ = 2(2(2(2T(1) + c * 2) + c * 2^2) + c * 2^3) + c * 2^4)$  
$ = d * 2^4 + c * 2^4 + c * 2^4 + c* 2^4 + c * 2^4$  
$T(2^0) = T(1)$  
$N = 2^k$  
$k = log(N)$  
$d * 2^k + k * c * 2^k$  
$d * 2^{log(N)} + 2^{log(N)} * c * log(N)$  
$d * N + N * c * log(N)$  
$\theta(N * log(N))$


##Algorithm #4

* Simpler to implement
* More efficient than the recursive version

```java
int maxSeqSum(int[] a) {
	int maxSum = 0, thisSum = 0;
	
	for (int j = 0; j < a.length; j++) {
		thisSum += a[j];
		
		if (thisSum > maxSum) {
			maxSum = thisSum;
		}
		else if (thisSum < 0){
			thisSum = 0;
		}
	}
	
	return maxSum;
}
```

##Mountains

* A mountain is a sequence of integers $x_s, x_{s+1}, ... x_t$
* if $x_s = x_t$ and there exists an integer $r$ such that $x_s < x_{s+1} < ... < x_r > x_{r+1} > ... > x_t$

Develop an efficient algorithm to solve the following problem: "Highest Mountain Subsequence Problem"

