#Algorithms 9/19/16

##Loop invariant

###Selection Sort

Loop Invariant: Before each iteration, $a_0 < a_1 < ... < a_{p-1}$  
**AND**  
$a_0, a_1, ..., a_{p-1}$ are the $p$ smallest elements of $a$.

This loop invariant doesn't prove correctness without knowing the code in the algorithm. For example, you could overwrite the original data in the input and it would be "sorted", but not what the user expects.