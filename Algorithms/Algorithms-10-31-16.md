#Algorithms 10/31/16

##Greedy Algorithms

Used to solve optimization problems  
Make decisions based on immediately available information  
Easy to invent and implement  
Efficient -- when they work.  
Not all problems can be solved by a greedy algorithm


##Common Features

* Chosen candidates and rejected candidates
* Solution function: do we have any solution?
* Feasibility function: can we extend our current solution?
* Selection function: greedily choose the next candidate
* Objective function: what to maximize?

In the makeChange example:

* Candidates are the set of coins
* Solution function checks total
* The change is feasible if it does not exceed amount
* Selection chooses highest-value coin remaining
* Objective function counts the number of coins used.


##The Knapsack Problem

The Knapsack problem has many different forms

We have $N$ objects and a knapsack  
Object $i$ has positive weight $w_i$ and positive value $v_i$

###The Fractional Knapsack

We will be allowed to break objects up into smaller pieces  
We can carry $x_i$ of object $i$, where $0 \leq i \leq 1$