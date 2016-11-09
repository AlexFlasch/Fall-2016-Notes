#Algorithms 11/7/16

##Service time

Let $\pi: \{0, 1, ..., N - 1\} \rightarrow \{0, 1, ..., N - 1\}$ be a one-to-one and onto function  
A "permutation" on the set $\{0, 1, ..., N - 1\}$

Service time for job $i: s_i = t_{\pi(i)}$

Total service time for order $\pi$:  
$N = 3$  
$T(\pi) = s_0 + (s_0 + s_1) + (s_0 + s_1 + s_2)$  
$ = 3s_0 + 2s_1 + s_2$  
$ = \sum\limits_{k=0}^{N-1} (N-k)s_k$  

###Example

Let $t_0 = 5, t_1 = 10, \text{and } t_2 = 3$  
$\pi(0) = 2, \pi(1) = 0, \pi(2) = 1$  
What is $T(\pi)$

$T(\pi) = \sum\limits_{k=0}^{N-1} (N - k)s_k$  
$ = 3s_0 + 2s_1 + s_2$  
$ = 3t_{\pi(0)} + 2t_{\pi(1)} + t_{\pi(2)}$  
$ = 3t_2 + 2t_0 + t_1$  
$ = 3(3) + 2(5) + 10$  


###Proof Idea

Suppose that $\pi$ **doesn't** arrange the jobs in order of increasing service time.  
Then there exists two indices $a$ and $b$, such that $a < b$, but $s_a > s_b$

Show that swapping jobs $a$ and $b$ will give a "better" $T$

Let $\pi^\prime = \pi$, except $\pi^\prime(a) = \pi(b)$ and $\pi^\prime(b) = \pi(a)$

$\pi = s_0, s_1, ..., s_a, ..., s_b, ..., s_{N-1}$  
$a < b$  
$s_a > s_b$  
$s_a = t_{\pi(a)}$  
$s_b = t_{\pi(b)}$  
$\pi^\prime(a) = \pi(b) \leftarrow$ shorter  
$\pi^\prime(b) = \pi(a) \leftarrow$ longer  
$T(\pi^\prime) < T(\pi)$

Show that $T(\pi) - T(\pi^\prime) > 0$  
What does this imply?

###Finish the proof

It suffices to show that $T(\pi) - T(\pi^\prime) > 0$

$T(\pi) = \sum\limits_{k=0}^{N-1} (N-k)s_k$  
$T(\pi) = \sum\limits_{k=0,k \neq a,k \neq b}^{N-1} (N-k)s_k + (N-a)s_b + (N-b)s_a$

$T(\pi)-T(\pi^\prime) = (N-a)s_a + (N-b)s_b - (N-a)s_b - (N-b)s_a$  
$ = Ns_a - as_a + Ns_b - bs_b - Ns_b + as_b - Ns_b + bs_a$  
cancel $Ns_a, Ns_b$  
$ = bs_a - as_a - bs_b + as_b$  
$ = (b-a)(s_a - s_b)$
$ > 0$ 