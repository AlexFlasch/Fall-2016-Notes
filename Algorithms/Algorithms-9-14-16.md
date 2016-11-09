#Algorithms 9/14/16

##Correctness

There is not "cookie-cutter" approach to proving correctness  
There is one recursive method, and one iterative method to prove correctness.  

###Recursive algorithms

* Try to use strong induction
* Let $P(N) = $"bsearch(a, l, r, x) is correct when $r - l = N$"
	* Can be abbreviated as "bsearch is correct when $r - l = N$"
* $N = 0$
* Then $r = l$
* Either $x$ is present, or not
* Assume that $P(N)$ is true for all $N < M$