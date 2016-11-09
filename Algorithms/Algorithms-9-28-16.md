#Algorithms 9/28/16

##Divide and Conquer

**Divide and conquer** is a basic algorithm design technique.  
Usually leads to efficient solutions. Solves problems recursively. Has 3 main steps:

1. Divide
2. Conquer
3. Combine

###Divide

Divide the problem into smaller non-overlapping sub-problems.


###Conquer

In the recusrive case, we have a base case which solves the sub-problems usually using brute force.


###Combine

Combine the solutions to the sub-problems into a solution to the original problem.


###Recurrences

A *recurrence* is a relationship defined in terms of itself. Its a natural way to characterize the running time of divide and conquer algorithms

Example:  
$T(N) = 2T(\frac{N}{2}) + \Theta (1)$  
$T(1) = \Theta (1)$  

$T(N) = T(N - 1) + \Theta (N)$  
$T(1) = \Theta (1)$


###Master theorem

The master theorem tells us the solution to recurrences of the form:  
$T(N) = a \cdot T(\frac{N}{b}) + f(N)$  
Where $a \geq 1$ and $b > 1$

$T(N) = a \cdot T(\frac{N}{b}) + f(N)$