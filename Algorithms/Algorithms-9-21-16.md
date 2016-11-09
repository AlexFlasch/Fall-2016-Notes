#Algorithms 9/21/16

##Asymptotic efficiency

* The running time of an algorithm on $N$ input items is given by $T(N)$
* The growth rate of $T(N)$ characterizes the efficiency of an algorithm
* Don't need to compute $T(N)$ exactly
* Asyomptotic behavior of T(N) = asymptotic efficiency of the algorithm
	* growth rate of $T(N)$ as $N$ goes to infinity.

### Running time as a funciton

* Asymptotic running time of an algorithm is defined in terms of functions whose domains are the set of natural numbers
	* $\mathbb{N} = \{ 0, 1, ... \}$  
* We usually asume: $T: \mathbb{N} \rightarrow \mathbb{R}^+$


###Asymptotic upper bound

* $O$-notation
* For functions $g(N)$ and $f(N)$, we say that $g(N)$ is an "asymptotic upper bound" of $f(N)$, written as $f(N) = O(g(N))$, if the following prposition is true: $P(f, g) = $ "There exist positive constants $c$ and $N_0$, such that, $0 \leq f(N) \leq c * g(N)$ for all for all $N \leq N_0$.


###Asymptotic lower bound

* $\Omega$-notation
* For functions $g(N)$ and $f(N)$, we say that $g(N)$ is an "asymptotic lower bound" of $f(N)$, written as $f(N) = O(g(N))$, if the following prposition is true: $P(f, g) = $ "There exist positive constants $c$ and $N_0$, such that, $0 \geq f(N) \geq c * g(N)$ for all for all $N \geq N_0$.


###Asymptotic tight bound

* $\Theta$-notation
* For functions $g(N)$ and $f(N)$, we say that $g(N)$ is an "asymptotic tight bound" if $f(N)$< written as $f(N) = \Theta(g(N))$, if $f(N) = O(g(N))$ and $f(N) = \Omega(g(N))$


###Not asymptotically tight

* $2N^2 = O(N^2)$ is asymptotically tight
* $2N = O(N^2)$ is not
* We use o-notation (little-o) to describe an upper bound that is not asymptotically tight.
* For functions $g(N)$ and $f(N)$, we say that $f(N)$ is little-o of $g(N)$, written as $f(N) = o(g(N))$, if the following is true: for any positive constant $c > 0$, there exists a constant $N_0$, such that, $0 \leq f(N) < c*g(N)$ for all $N \geq N_0$.
* What is the main difference between $O$ and $o$? With little-o there is always a value that meets the threshold no matter the constant $c$.
* In $o$-notation, $f(N)$ becomes negligible, relative to $g(N)$ as $N$ goes to $\infty$.
* In other words, $f(N) = o(g(N))$ if $lim_{N \rightarrow \infty} \frac{f(N)}{g(N)} = 0$


