#Algorithms 10/21/16

##Amortization

$\hat{c}_i =$ amortized cost of $i^{th}$ op  
$c_i = $ actual cost of $i^{th}$ op

**Need:** $\sum\limits_{i=1}^N \hat{c}_i \geq \sum\limits_{i=1}^N c_i$

###Stack operations

<style>
.container {
	display: flex;
	justify-contents: space-between;
}

.column-2 {
	width: 50%;
}
</style>

<div class="container">
	<div class="column-2">
		<b>Actual costs of operations:</b>  <br/>
		Push: 1  <br/>
		Pop: 1  <br/>
		multiPop: min(k,s) <br/>
	</div>
	<div class="column-2">
		<b>Amortized costs of operations:</b>  <br/>
		Push: 2  <br/>
		Pop: 0  <br/>
		multiPop: 0 <br/>
	</div>
</div>


###Accounting analysis

Since the push costs 2, it will pay for any pop or multiPop that can happen.

Credit can never be negative. So credit must be follow: $\sum\limits_{i=1}^N \hat{c}_i - \sum\limits_{i=1}^N c_i \geq 0$


###Potential analysis

A potential function $\Phi$ maps each data structure $D_i$ to a real number $\Phi(D_i)$  
Amortized cost of $c_i$, with respect to $\Phi$, is $\hat{c}_i = c_i + \Phi(D_i) - \Phi(D_{i-1})$  
The amoritzed cost is the actual cost plus potential.

$\sum\limits_{i=1}^N \hat{c}_i = \sum\limits_{i=1}^N (c_i + \Phi(D_i) - \Phi(D_{i-1})$  
$c_N + \Phi(D_N) - \Phi(D_0)$  
$(\sum\limits_{i=1}^N c_i) + (\Phi(D_N) - \Phi(D_0))$

For every operation we want $\Phi(D_i) \geq \Phi(D_0)$ and $\Phi(D_i) \geq 0$ to be true.


###Potential for stack operations

Let $\Phi(S) =$ # of elements in the stack  
$\Phi(D_0) = 0$

The number of objects in the stack can never be negative, so we have $\Phi(D_i) \geq 0$ and $\Phi(D_i) = \Phi(D_0)$

$\Phi(D_0) = 0 and \Phi(D_i) \geq \Phi(D_0)$  
Thus, total amortized cost for $N$ operations is an upper bound on total actual cost of $N$ operations.

We must compute amortized costs for each operation.

###Push

Operation $i$ is push  
$c_i = 1$  
Amortized cost: $\hat{c}_i = c_i + \Phi(D_i) - \Phi(D_{i-1})$  
Thus: $\hat{c}_i = 1 + \Phi(D_i) - \Phi(D_{i-1})$  
$ = 1 + (S + 1) - S$  
$ = 2$

Pop is mostly the same, except instead of $1 + (S + 1) - S$ you have $1 + (S - 1) - S$ since you're removing an element from the stack, and so you end up with an amortized cost of 0.


###MultiPop

Operation $i$ is multiPop  
$c_i = min(S, k)$  
Amortized cost: $\hat{c}_i = c_i + \Phi(D_i) - \Phi(D_{i-1})$  
Thus: $\hat{c}_i = min(S, k) + (S - min(S, k)) - S$  
$ = 0$