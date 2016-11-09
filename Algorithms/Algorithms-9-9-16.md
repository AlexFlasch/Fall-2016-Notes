#Algorithms 9/9/16

##Maximum Subsequence Sum Problem

Find the maximum value of $S = \sum_{ i \leq k \leq j }$  

* Note that $S = x_i + x_{ i + 1 } + ... + x_j$

Example: for input -2, 11, -4, 13, -5, -2, what is the answer?

Answer: 20 ($x_1$ through $x_3$)

###Brute force algorithm

```java
int maxSubSumN(int[] a) {
	int maxSum = 0;
	
	for (int i = 0; i < a.length; i++) {
		for (int j = i; j < a.length; j++) {
			int thisSum = 0;
			
			for (int k = 1; k <= j; k++) {
				thisSum += a[k];
			}
			
			if (thisSum > maxSum) {
				maxSum = thisSum;
			}
		}
	}
}

return maxSum;
```

* Runtime: $O(N^3)$


####Solving the runtime

1. $\sum\limits_{i=0}^{n-1} \sum\limits_{j=i}^{n-1} \sum\limits_{k=i}^{j} 1$  
2. isolate $\sum\limits_{k=i}^{j}1$
3. $\sum\limits_{k=i}^{j} = j - i + 1$
4. isolate $\sum\limits_{j=i}^{n-1}$
5. $\sum\limits_{j=i}^{n-1} (j-i+1) = 1 + 2 ... + (n-i)$
6. $ = \frac{(n-i)(n-i+1)}{2}$
7. $\sum\limits_{i=1}^{n} = \frac{n(n+1}{2}$
8. isolate $\sum\limits_{i=0}^{n-1}$
9. $\sum\limits_{i=0}^{n-1} (\frac{(n-i)(n-i+1)}{2})$


###Lookup table algorithm

* Don't recompute values that have already been computed

```java
int maxSubSumN(int[] a) {
	int maxSum = 0;
	
	for (int i =0; i < a.length; i++) {
		int thisSum = 0;
		
		for (int j = i; j < a.length; j++) {
			thisSum += a[j];
			
			if (thisSum > maxSum)
				maxSum = thisSum;
		}
	}
	
	retunr maxSum;
}
```
* Runtime: $\theta(N^?)$

###Divide and conquer algorithm

* Recursive and complicated!

Divide and conquer: split input up into two (roughly) equal halves

```java
int maxSumRec(int[] a, int l, int r) {
	if (l == r) {
		if (a[l] > 0) {
			return a[l];
		}
		else {
			return 0;
		}
	}
	
	int mid = (l + r) / 2,
		maxl = maxSumRec(a, l, mid),
		maxr = maxSumRec(a, l, mid);
		
	int maxBorderl = 0, sum = 0;
	
	for (int i = mid; i >= l; i--) {
		sum += a[i];
		if (sum > maxBorderl)
			maxBorderl = sum;
	}
	
	int maxBorderr = 0;
	
	for (int i = mid; i <= l; i++) {
		sum += a[i];
		if (sum > maxBorderr)
			maxBorderr = sum;
	}
	
	return Math.max(Math.max(maxl, maxr), ?? );
}
```

$T(N)$ = time required to solve problem with N input elements  
$T(1) = 1$  
$T(N) = T(N/2) + T(N/2) + O(N)$  
    $= 2T(N/2) + O(N)$

####Cases to consider

* The max subsequence is either:
	* in the left half,
	* in the right half,
	* or crosses the middle and is in both halves
* Example: 4, -3, 5, -2 | -1, 2, 6, -2
* Answer: ??? (11?)
* Assume $N = 2^k$