#Algorithms 11/2/16

##Fractional Knapsack

We are allowed to break objects up into smaller pieces  
We can carry $x_i$ of object $i$, where $0 \leq x_i \leq 1$  

Maximize: $\sum\limits_{i=0}^N x_i v_i$  
Subject to: $\sum\limits_{i=0}^N x_i w_i$  

We get to pick the $x_i$ values  
We are given $v_i$ and $w_i$ values.

###Observations

In the optimal solution, $S = \sum\limits_{i=0}^N x_i w_i = W$  
We should always try to have $x_i = 1$  
If $x_i \leq 1$, then adding $x_i w_i$ to the knapsack should make $S = W$


###The greedy algorithm

```java

// w.length == v.length
static double[] knapsack(int[] w, int[] v, int W)
{
	double[] x = new int[w.length];
	int weight = 0;
	while (weight < W)
	{
		int i = ?? // Object i
		if (weight + w[i] <= W)
		{
			x[i] = 1;
			weight += w[i];
		}
		else
		{
			x[i] = (W - weight) / (double)w[i];
			weight = W;
		}
	}
	return x;
}

```


###Optimaity

Is our greedy algorithm optimal?

Theorem: If objects are selected in order of decreasting $\frac{v_i}{w_i}$, i.e. $\frac{v_0}{w_0} \geq \frac{v_1}{w_1} \geq ... \geq \frac{v_{n-1}}{w_{n-1}}$ then the knapsack finds an optimal solution.


###Proof idea

Let $X = (x_0, x_1, ..., x_{n-1})$ be a solution found by our algorithm  
Let $Y = (y_0, y_1, ..., y_{n-1})$ be **any** solution  
Assum $X \neq Y$  
Let $V(X) = \sum\limits_{i=0}^N x_i v_i, V(Y) = \sum\limits_{i=0}^N y_i v_i$  
Show that $V(X) \geq V(Y)$

####Step 1

If $x_i = 1$ for $i = 0, 1, .., N-1$, then $X$ is clearly optimal  
Thus, going forward, let $j$ be the smallest index such that $x_j < 1$.


####Step 2

For $i < j$, the algorithm picks $x_i = 1$, meaning you're adding the whole item  
For $i > j$, the algorithm picks $x_i < 1$, meaning you're adding a fraction of an object  


####Step 3

When knapsack returns, the capacity of the knapsack is always what?  
**Answer**: $\sum x_i w_i = W$


####Step 4

Since $Y$ is a feasible solution, how does $\sum\limits_{i=0}^N ???$


####Step 5

$\sum\limits_{i=0}^N (x_i - y_i)w_i$


####Step 6

X = $(x_0, x_1, ..., x_j, ..., x_{n-1}$  
Y = $(y_0, y_1, ..., y_j, ..., y_{n-1}$

$V(X) = \sum v_i x_i$  
$V(Y) = \sum v_i y_i$  
$V(X) \geq V(Y) \rightarrow X$ is optimal

$\sum w_i x_i = W$  
$\sum w_i y_i \leq W$  

$V(X) - V(Y) \geq 0$  
$ = \sum v_i x_i - \sum v_i y_i$  
$ = \sum (x_i - y_i) v_i$  
$ = \sum (x_i - y_i) v_i (1)$  
$ = \sum (x_i - y_i) v_i (\frac{w_i}{w_i})$  
$ = \sum [(x_i - y_i) \frac{v_i}{w_i}] w_i$

$(x_i - y_i) \frac{v_i}{w_i} ? (x_i - y_i) \frac{v_j}{w_j}$  
$i < j: \geq$  
$i = j: \geq$  
$i > j: \geq$