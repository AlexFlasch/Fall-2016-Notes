#Algorithms 11/9/16

##Safe Edge

$A$ is a subset of edges of some graph  
If $A$ is a subset of an MST, then we say that $(u, v)$ is a **safe edge** for $A$ if $A \cup \{(u, v)\}$ is also a subset of an MST

##Growing minimum spanning trees

```java
private HashSet<Edge> generic_MST()
{
	HashSet<Edge> a = new HashSet<Edge>();
	while (!spanning_tree(a))
	{
		Edge e = getSafeEdge(a);
		a.add(e);
	}
	return a;
}
```

##How to choose a safe edge?

We will prove a theorem that will help us recognize safe edges  
First we need to define some terms.

* A **cut** of an undirected graph $G = (V, E)$ is a partition of $V$ into two disjoint, non-empty subsets, i.e., $C = (S, V - S)$.
* A **cross** is an edge that crosses a cut.
* A cut $(S, V - S)$ **respects** a set $A \subseteq E$ if no edge crosses the cut.
* A **light edge** is the edge that crosses a cut $C$ with the least weight.

An edge being added is **safe** if that edge does not break the MST. ($A \cup \{ (u, v) \} \subseteq T^\prime$)

###Theorem

Let $G = (V, E)$ be a connected, undirected graph with weight function $w$.  
Let $T$ be an MST of $G$.  
Let $A \subseteq T$.  
Let $C = (S, V - S)$ be a cut of $G$ taht respects $A$.  
Let $(u, v)$ be a light edge crossing $C$.  
Then $(u, v)$ is safe for $A$.

##Proof

Construct another MST $T^\prime$ that includes $A \cup \{ (u, v) \}$ by using a "cut and paste" argument  
That is, we will cut out one *other* edge and paste in $(u, v)$ *in its place* to make $T^\prime$.

###What if $T$ contains $(u, v)$?

$\therefore (u, v)$ is safe for $A$  
Definition of safe: $A \cup \{ (u, v) \} \subseteq T^\prime$

Answer: We're done. If $T$ contains $(u, v)$ its a trivial problem.

###What if $(u, v) \notin T$?

####Construction of $T^\prime$

Let $p$ be the unique simple path from $u$ to $v$ in $T$  
There exists $(x, y)$ on $p$ and $(x, y)$ crosses $C$  
$(x, y) \neq (u, v)$  
Removing $(x, y)$ breaks $T$