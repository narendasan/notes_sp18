# ECE 498LV - Neuronal Networks 
__Path__: Any sequence of vertices s.t. every consecutive pair in the sequence is the connected by an edge (in the case of directed graphs, w.r.t arrows) 
__Length of Path__: # of edges in the sequence 

Consider a simple unweighted network with $A_{ij}$ to find set of paths

If the product of $A_{ij}$ and $A_{jk}$ is 1 then there is a length-2 path from $i$ to $k$ through $j$ else if 0 there is no path

The total number of $N_{ik}^{(2)}$ of paths of length 2 from $i$ to $k$ via any $j$ is $N_{ik}^{(2)} = \sum_{k=1}^{n} A_{ij} A_{jk} = [A^2]_{ik}$

__Length 3 paths__ : $N_{il}^{(3)} = \sum_{k,l=1}^{n} A_{ij} A_{jk}A_{kl} = [A^3]_{il}$
__Length r paths__: $N_{il}^{(r)} = [A^r]_{il}$ 

Special case of __counting loops__: $[A^r]_{ii}$ would be # loops of length $r$ at node $i$ 

Total loops of length $r$:
$L_r = \sum_{i=1}^{n} [A^r]_{ii} = Tr(A^r)$
(Counts loops with same vertices but different starting points separately)

__# of triangles__ $L_3 = Tr(A^3)$
__Geodesic Path__: Shortest Path 
Is path between 2 nodes s.t. there is no shortest path (len == geodesic distance) 

__Closure__: Path $u$,$v$,$w$ is closed if third edge from u to w exists
__Clustering Coeffiecient__: Fraction of paths of length 2 that are closed 

$$
C = \frac{\text{# of closed path of length 2}}{\text{# paths of path of length 2}}
$$

$$
 = \frac{L_3}{L_2}
$$

$$
= \frac{\text{# of triangles} * 3 }{ \text{# of connected triples}}
$$

 

Networks are __small world__ if large C and small average path