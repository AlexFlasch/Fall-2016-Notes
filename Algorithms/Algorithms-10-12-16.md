#Algorithms 10/12/16

##Reading

p147 - 150  
7.1 and 7.2


##Quicksort

* Fastest known sorting algorithm in practice
* Best case: $O(N log(N))$
* Worst case: $O(N^2)$
* Simple to understand
* Easy to prove correct
* Divide and conquer


* Quicksort sorts a sub array of integer values: a[p..r]
	* a[p], a[p+1], ..., a[r]
* Divide
	* First, partition the array into two (possibly empty) sub arrays
	* a$_{left}$ = a[p..q-1] and a$_{right}$ = a[q+1..r]
	* such that every element in a$_{left}$ is at most a[q] and a[q] is less than or equal to every element in a$_{right}$
* Conquer: Recursively sort a$_{left}$ and a$_{right}$
* Don't really need a combine step.

```java
void qsort(int[] a, int p, int r) {
	if (p < r) {
		int q = partition(a, p, r);
		qsort(a, p, q - 1);
		qsort(a, p + 1, r);
	}
}

int partition(int[] a, int p, int r) {
	int x = a[r]; // pivot element
	int i = p - 1;
	for (int j = p; j < r; j++) {
		if (a[j] <= a[r]) {
			i++;
			swap(a, i, j);
		}
	}
	swap(a, i + 1, r);
	return i +1;
}	
```

##Analysis

###Worst case

* Performance depends on choice of pivot element
* Balanced partitions are the good choice, and unbalanced partitions are the bad choice.
* T(N) = running time for qsort
* T(N) = T(q) + T(N - q - 1) + $\Theta$(N)
* T(0) = O(1)
* What is the worst case for our qsort?
* Totally unbalanced partitions means, at every level, one partition has size 0
* T(N) = T(N-1) + $\Theta$(N)
* 		= T(N-1) + $\Theta$(N)
* You can solve these to get T(N) = $\Theta(N^2)$


###Best case

* Totally balanced partitions are the best case
* For the sake of simplicity, assume N = 2^k + 1
* The Master theorem case 2 says that T(N) = $\Theta$(N log N)
* Any split of "constant proportionality" also gives T(N) = $\Theta$(N log N)


###Average case

* T(N) = T(q) + T(N - q - 1) + c * N
* Assume all pivot values are equally likely
	* Each pivot value q has a probability of 1/N
* Compute average value of T(q), for q = 0, 1, ..., N -1