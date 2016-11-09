#Algorithms 9/7/2016

###Model of Computation

* Sequential, random-access-machine
* Simple instructions: add, multiply, compare, assign, etc
* One unit of time required to do simple operations
* Fixed size integers
* No fancy operations: matrix operations, sorting, etc
	* Any "fancy" operations must be implemented using simple instructions by the programmer


###What do we analyze?

* Runtime and correctness
* Runtime: the number of simple operations executed for an input of size N
* Worst-case Runtime: the longest runtime for any input of size N.
* Best-case Runtime: the shortest runtime for any input of size N.
	* Best case too optimistic, rarely used


###Input size

* Depends on the problem being studied
* Usually the number of input items
* Sometimes the total number of bits needed
* Sometimes the value of a number
* Sometimes two numbers (for example number of nodes and edges)
* Indicate which size measure used with each problem