# ECE 498LV - Lecture 4

###  Knowledge Networks

#### Citation Networks

Conversion of Directed Networks in to Undirected for analysis 

#### Cocitation

- Cocitation $i$ and $j$ are # of verticies that have outgoing edges that point to $i$ and $j$ i.e. # papers that cite both $i$ and $j$ 

  - $A_{ik}A_{jk} = 1$ if $i$ and $j$ both are cited by $k$, 0 otherwise
  - $C_{ij} = \sum_{k=1}^{n}A_{ik}A_{jk} = \sum_{k=1}^{n}A_{ik}A_{kj}^T$ wher $A_{kj}^T$ is the $(k,j)$ element of $A^t$

- Define the Cocitation matrix as 
  $$
  C = AA^T\\
  C^T = (AA^T)^T = AA^T = C
  $$
  So it is symmetric

  If the diagaonal elements of $C$ are ignored, adjacencey matrix of cocitatiion network, (undirected since $C$ is symmetric)

  Strong cocitation $\implies$ similar topic 

#### Citometrics

$\rightarrow$ Study of citation networks 

##### H-Index

_H-Index_ aims to define productivity based on the number of papers written and the number of citations



Let $f$ be the function corresponding to the # of citiation for each publication. Then for papers indexed by $i$
$$
h = \max\limits_{i} min (f(i),i)
$$

####  Bibliographic Coupling

$\rightarrow$ Opposite of cocitation  

\# of vertices to which both $i$ and $j$ point
$$
B_{ij} = \sum_{k=1}^{n} {A_{ki}A_{kj}} = \sum_{k = 1}^{n}{A_{ik}}^TA_{kj}\\
\text{so } B = A^TA
$$


$B_{ii}$ is # of papers that $i$ cites 

$B$ $\implies$ notiion of similarity 

$B$ is a better indicatior of similarity than $C$ so is used for recomendation engines 

$B$ is a fixed value but $C$ changes with the number of new papers being pubished 



## Search

#### Hubs and Authorities

Two kinds of important nodes in directed networks 

- **Authorites** $\rightarrow$ nodes that contain useful informtion about a topic 
- **Hubs** $\rightarrow$ nodes that tell use where the best authorities are 

Nodes can be both hubs and authorities 

##### Hyperlink - Induced Topic (HITS) Algorigthm

**HITS** give each vertex $i$ an authority score $x_i$ and a hub score $y_i$

​	$\implies$ We want $x_i$ to be large if pointed to by many hubs 

​	$\implies$ We want $y_i$ to be large if pointed to by many authorites 
$$
x_i = \alpha \sum{A_{ij}y_j} \text{ where $\alpha$ is a constant}\\
y_i = \beta \sum{A_{ji}x_i} \text{ where $\beta$ is a constant}\\
$$

$$
\vec{x} = \alpha A \vec{y} \\
\vec{y} = \beta A^T \vec{x} 
$$

$$
AA^Tx = \lambda x \text{ and } A^TAy = \lambda y \text{ where } \lambda = \frac{1}{\alpha \beta}\\
Cx = \lambda x \quad By = \lambda y
$$

So the **hub** score $\vec{y}$ is the eigenvector of bibliographic coupling matrix (including diagonal) **authority** score $\vec{x}$ is the eignevectetor of the cocitation matric (inc. diagonal ) $\implies$ want the eigenvect coresponding to the largest eigenvalues.

Note that we need the same eigenvalue $\lambda$ in both cases 

$B$ and $C$ are cospacial $\therefore$  have the same eigen values 
$$
AA^T x = \lambda x \\
A^T AA^Tx = A^T\lambda x \text{ by left mult by} A^T\\
(A^TA) (A^Tx) = \lambda (A^Tx)
$$
so $A^Tx$ is eigenvector of $A^TA$ with same eigenvalue $\lambda$ 

Further $y = A^Tx$ so get result 



$\lambda \sum_{i} w_i^2​$

\frac{\sum_{i = 1}^{n}\sum_{j = 1}^{n}\sum_{k = 1}^{n} \mathbf{A}_{ij}\mathbf{A}_{jk}\mathbf{A}_{ki}}{6}$

