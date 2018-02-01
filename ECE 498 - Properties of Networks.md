# Properties of Networks

| Local Properties       | Global Properties   |
| ---------------------- | ------------------- |
| degree                 | Chromatic Number    |
| clustering coefficient | bipartness          |
| subgraph distribution  | average path length |

## Degree

__Degree__ of a vertex is the # of edges connected to it

degree if a vertex is $k_i$

for undirected networks $k_i = \sum_{j = 1}^{n} A_{ij}$

if $m$ edges in network, then there are $2m$ edges of edges 
$$
2m = \sum_{i = 1}^{n}k_i
$$

$$
m = \frac{1}{2} \sum_{i = 1}^{n}k_i =\frac{1}{2}\sum_{i}\sum_{j}A_{ij}
$$

The mean degree $C$ is 
$$
C = \frac{1}{n}\sum_{i =1}^{n}k_i = \frac{2m}{n}
$$
max number of edges in network of size $n$: 
$$
\binom{n}{2} = \frac{n(n-1)}{2}
$$


Density $\rho$ of a network is fraction of edges actually present 
$$
\rho = \frac{m}{\binom{n}{2}} = \frac{2m}{(n)(n-1)!} = \frac{C}{n-1}
$$


A network for which $\rho \rightarrow constant$ as $n \rightarrow \infty$ is *dense* 

$p \rightarrow 0$ as $n \rightarrow \infty$ is sparse

(sparse if $c\rightarrow constant$ as $n \rightarrow \infty$)



Asymtotic notiions require a sequence of networks which fine theoretically, but bad practically. 

Some networks like WWW or internet do grow (but still sparse)

 

Some netowkrs have vertices with the same degree 

**Regular Graphs**, k - regular 

infinite latices 

![Screen Shot 2018-01-30 at 11.24.58 AM](/Users/naren/Documents/notes_sp18/assets/Screen Shot 2018-01-30 at 11.24.58 AM.png)





### Directed Networks

#### In-degree

\# of incomming edges

#### Out-degree

\# number of outgoing edges

recall $A_{ij} =1$ if edge from $j$ to $i$
$$
k_i^{in} = \sum_{j = 1}^{n} A_{ij}
$$

$$
k_j^{out} = \sum_{i= 1}^{n} A_{ij}
$$

##__Degree distribution__:

Over all nodes 

$\rho_k$ is the imperical distribution of the degree

#### Power Law Distibution

$$
\rho_k \sim k^{-\gamma}
$$



where $\gamma$ is the power-lay expoenet (allometric scalling)
$$
log\rho_k \sim - \gamma log  k
$$
so $\gamma$ is slope along log-log plot 

for directed networks 


$$
\rho_{k,in}\sim k^{-\gamma_in}
$$

$$
\rho_{k,out}\sim k^{-\gamma_out}
$$
Since degress are $\mathbb{Z}^+$ normalization to get an emperical probability 
$$
\sum_{k=1}^{\infty} \rho_k= 1
$$
Let $\rho_k = Ck^{-\gamma}$, $C\sum_{k=1}^{\infty}k^{-\gamma} = 1$

so $C = \frac{1}{\sum_{k=1}^{\infty}k^{-\gamma}}$ = $\frac{1}{\zeta(\gamma)}$

Where $\zeta(\gamma)$ is the Riemann Zeta Function 

so $\rho_k = \frac{k^{-\gamma}}{\zeta(\gamma)}$ 



##### Continuous Approx.

In analictical work oftine allow approximation to be any positive value
$$
\rho(k) = Ck^{-\gamma}
$$

$$
normalize \int_{k_{min}}^{\infty}\rho(k)dk = 1, \text{so } C= \frac{1}{\int_{k_{min}}^{\infty}k^{-\gamma}dk }\\
= (\gamma -1 ))k_{min} ^ {\gamma -1}\\
\rho(k) = (\gamma - 1)k_{min} ^ {\gamma -1}k^{-\gamma}
$$

where $k_{min}$ is the smallest degree 



### ML Estimation for exponential mean $\lambda$

Likelyhood function from data 


$$
L(\lambda, x_1,x_2,..., x_n) = \prod_{j=1}^{n}f_x(x,\lambda) \\
= \prod_{j=1}^{n}\lambda e^{-\lambda x_j}
= \lambda^n exp(-\lambda\sum_{j=1}^{n}x_j)
$$
Log-Likelyhood 

take logs
$$
 \mathbb{l} (\lambda, x_1,x_2,..., x_n) = lnL\\
 = ln(\lambda^n) + ln(exp(-\lambda\sum_{j=1}^{n}x_j))\\
 = nln\lambda - \lambda\sum_{j=1}^{n}x_j
 
$$

$$
\hat{\lambda} = argmin_{\lambda} \mathbb{l} (\lambda, x_1,x_2,..., x_n)
$$
so take derivitive and set to 0 
$$
\frac{d}{dx}\big(nln\lambda - \lambda \sum_{j=1}{n}x_j\big) \\
= \frac{n}{\lambda} - \sum_{j =1}{n}x_i = 0\\
\hat{\lambda} = \frac{n}{\sum_{j=1}^{n}x_{ij}}
$$

## Perferential Attachment 

Start $m_0$ nodes with aribitrary edges (as longals connected so seach node has at least one edge)

__growth, preferential attachment__

At each timestep add a new node with $m \leq m_0$ edges that connect new node to $m$ nodes already in the network 



Probaility $\Pi(k)$ that edge of networks connects to node $i$ depends on degree $k_i$ as 
$$
\Pi(k_i) = \frac{k_i} {\sum_jk_j}
$$




 















