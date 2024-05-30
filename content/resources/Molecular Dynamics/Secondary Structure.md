A **Secondary Structure** on a sequence $(a_i)_{1\le i \le n}$ is a subset of $S \subset \{i:1\le i \le n\} \times \{i: 1 \le i \le n\}$. It is known that for all $(i,j)$ and $(k.l)$ in $S$ that 
$$i =k \iff j = l \tag{1}$$
$$k < j \implies i < k < l < j \tag{2}$$
The relation $(1)$ specifies that each nucleotide takes part in at most one base pair, while the second condition forbids [[Knots in RNA|knots and pseudo-knots]]. The base-pair $(k,l)$ is called [[Interior Base Pair|interior]] to $(i,j)$ if the relation $(2)$ holds. 

Meanwhile, for $r$ between the base pair $(i,j)$ such that $i< r < j$ but if $S$ contains no pair $x, y$ s.t. $i <x < r < y < j$, the base $r$ is defined as [[Accessible Bases|accessible]] from $(i, j)$. 
