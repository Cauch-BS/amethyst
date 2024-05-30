ViennaRNA uses dynamic programming to find minimum free-energy secondary structures or partition functions of RNA molecules. Furthermore, an inverse folding heuristic is implemented to determine sets of structurally neutral sequences. 
# Principles Underlying ViennaRNA

A [[Secondary Structure|secondary structure]] on a sequence $(a_i)_{1\le i \le n}$ is a subset of $S \subset \{i:1\le i \le n\} \times \{i: 1 \le i \le n\}$. It is known that for all $(i,j)$ and $(k.l)$ in $S$ that 
$$i =k \iff j = l \tag{1}$$
$$k < j \implies i < k < l < j \tag{2}$$
The relation $(1)$ specifies that each nucleotide takes part in at most one base pair, while the second condition forbids knots and pseudo-knots. The base-pair $(k,l)$ is called [[Interior Base Pair|interior]] to $(i,j)$ if the relation $(2)$ holds. 
## Finding the Minimal Free Energy
We can find the minimum free-energy  using the following pseudo code:

```python
for i in range(1, n):
	for j in range(i+1, n + 1):
		minimal_energy_if_paired(i, j) = min(
			# if no base pairs interior to (i,j)
			energy_of_hairpin(i, j),
			# if there exists exactly one branch to the loop interior to (i,j)
			min([energy_of_loop(i,j : p,q) + minimal_energy_if_paired(p, q) for p in range(i + 1, j) for q in range(p + 1, j)])
			# for multiple branched loops
			min([min_energy_of_multiloop(i+1, k) + min_energy_of_multiloop(k+1, j-1) + cc for k in range(i+2, j-2)]) 
			#cc is the base term where free_energy = cc + ci * (number of interior base pairs) + cu * (unpaired)
		)
		
		min_energy_of_multiloop = min(
			minimal_energy_if_paired(i,j) + ci, # exactly one interior base pair
			min_energy_of_multiloop(i+1, j) + cu, #i+1 is unpaired
			min_energy_of_multiloop(i, j-1) + cu, #j-1 is unpaired
			min([min_energy_of_multiloop(i, k) + min_energy_of_multiloop(k+1, j) for k in range(i + 1, j)]) #all other cases
		)

		minimum_free_energy(i,j) = min(
			minimal_energy_if_paired(i,j),
			[minimum_free_energy(i, k) + minimum_free_energy(k, j) for k in range(i+1, j)], 
		)

minimum_free_energy = minimum_free_energy(1,n)
```

[[Decomposition of Secondary Structures of RNA|What is a multiloop? How does this code work?]]

Dangling, terminal ends are not considered in this code. 
## Finding the Partition Function
The partition function $\mathcal{Q}$ for every structure $S$ can be expressed as 
$$ \mathcal{Q} = \sum_{s \in S} \exp\left(-\dfrac{\Delta G(s)}{RT}\right) $$
Then the partition function can be found by similar principles. 

```python
def maxwell_factor(x, T):
	return exp(-x/RT)

for i in range(1, n + 1):
	for j in range(i + 1, n + 1):
		j = i + d
		partition_of_subseq_with_paired(i,j) = 
			maxwell_factor(energy_of_hairpin(i, j), T) + 
			sum([maxwell_factor(energy_of_loop(p, q), T) * partition_of_subseq_with_paired(p, q)]) + 
			sum([partition_of_subseq_with_multiloop_left(i+1, k-1) * partition_of_subseq_with_multiloop_right*(k, j-1) * maxwell_factor(cc, T) for k in range(i+2, j-1)])
			
		partition_of_subseq_with_multiloop_left(i, j) = sum([
			(maxwell_factor((k-i)*cu, T) + partiton_of_subseq_with_multiloop_left(i, k-1)) * partition_of_subseq_with_multiloop_right(k, j)
			for k in range(i+1, j)
		])
		
		partition_of_subseq_with_multiloop_right(i,j) = sum([
			partition_of_subseq_with_paired(i,k) * maxwell_factor((j-k)*cu, T)*maxwell_factor(ci, T)
			for k in range(i+1, j+1)
		])
		
		partition_of_subseq(i, j) = 1 + partition_of_subseq_with_paired(i,j) + 
		sum([partition_of_subseq(i, p-1) * partition_of_subseq_with_paired(p,q) for p in range(i+1, j) for q in range(p+1, j)])

total_partition = partition_of_subseq(1, n)
```

## Solving Inverse Folding
Inverse folding is used to find sequences that form a predefined structure, or to search for sequences for which the probability of the structure being observed is greater than some threshold $p$. 

The approach is to modify an initial sequence $I_0$ so as to minimize a cost function given by the “structure distance” $c(I) = d(S(I), \mathscr{T})$ between the structure $S(I)$ and the target structure $\mathscr{T}$. $I_0$ is modified by means of an adaptive walk, where a random mutation is accepted if a cost function decreases. A mutation is performed on unpaired base pairs in $I$ or exchanging two compatible base pairs (G and C $\to$ C and G)

To minimize the chance of getting stuck in a local minimum, and the amount of computation in calculating the number of foldings, the authors start from a hairpin (which constitutes a *substructure*) and finds the corresponding subsequence. The sequence is then elongated by 1bp until a *loop* is reached. 
