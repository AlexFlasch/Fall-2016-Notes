#Algorithms 10/5/16

##2D Peak finding

###First approach

1. Look at the center column, find its max.
2. If its a peak, return it.
3. Otherewise if left neighbor is bigger, search left half
4. Otherwise, search right half
5. Base case is when 


###Efficiency

Recurrence: $T(W, H) = T(\frac{W}{2}, H) + \Theta(H)$  
$T(1, H) = \Theta(H) = c \cdot H$  
$T(W, H) = T(\frac{W}{2}, H) + c \cdot H$  
$ = T(\frac{W}{4}, H) + c \cdot H + c \cdot H$  
$ = T(\frac{W}{8}, H) + c \cdot H + c \cdot H + c \cdot H$  
...
$\Theta(H \cdot log W)$


###Second approach

1. Look at boundary window
2. Find global max within the boundary window.
3. If its a peak, return it.
4. Otherwise, find larger neighbor.


###Efficiency

$T(N) = T(\frac{N}{2}) + \Theta(N)$

$a = 1, b = 2, log_2 1 = 0$  
$f(N) = \Theta(N)$  
$f(N) = \Omega(N^{log_b a+\epsilon})$


##Practice

```java
int minRec(int[] a, int l, int r) {
	if(l == r - 1)
		return a[l];
	int mid = (l + r) / 2,
		minl = minRec(a, l, mid)
		minr = minRec(a, mid, r);
	if(minl < minr)
		return minl
	return minr;
```

$T(N) = 2T(\frac{N}{2}) + \Theta(1)$  
$a = 2, b = 2 \rightarrow log_b a \rightarrow log_2 2 = 1$
