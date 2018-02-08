



# ECE 498 LV Lecture 7 - Network Dynamics

Modeling with differential equations 

$x_1[t], x_1[n] \sim$ difference equation
$$
\begin{bmatrix}
x_1[n+1] \\
...\\
x_N[n+1] \\
\end{bmatrix}
=
f\Big(\begin{bmatrix}
x_1[n] \\
...\\
x_N[n] \\
\end{bmatrix}\Big)
$$
Used in Syncronization and Consensus 



Consider dynamics on networks defined by diff eqs. 

Simplest setting is first order linear systems


$$
{x_1}' = p_{11}(t)x_1 + p_{12}(t)x_2 + ...+p_{1n}(t)x_n + f_1(t) \\
{x_2}' = p_{21}(t)x_1 + p_{22}(t)x_2 + ...+p_{2n}(t)x_n + f_n(t) \\
...\\
{x_n}' = p_{n1}(t)x_1 + p_{n2}(t)x_2 + ...+p_{nn}(t)x_n + f_n(t) \\
$$
Define a coefficent matrix 
$$
P(t) = \Big[p_{ij}(t)\Big]
$$


and columns vectors $\mathbf{x} = \Big[x_{i}(t)\Big], \mathbf{f}(t) = \Big[f{i}(t)\Big]$

Then first-order linear system 
$$
\frac{\partial x}{\partial t} = P(t)\mathbf{x} + \mathbf{f}(t)
$$
A __solution__ on the open interval $\mathbb{I}$ is a column vector function $\mathbf{x} = \Big[x_{i}(t)\Big]$ s.t. component functions of $\mathbf{x}$ statisfy the system of equations identically on $\mathbb{I}$



If all $\Big\{p_{ij}(t)\Big\} and \Big\{f_i(t)\Big\}$ are continuous on $\mathbb{I}$, then there is a **unique** solution $\mathbf{x}(t)$ on $\mathbb{I}$ satisfying the preassigned interval



Consider the small network ![Screen Shot 2018-02-06 at 11.21.54 AM](/Users/naren/Documents/notes_sp18/assets/Screen Shot 2018-02-06 at 11.21.54 AM.png) 
$$
{x_1}' = 4x_1 - 3x_2\\
{x_2}' = 6x_1 -7x_2

$$

$$
\frac{\partial x}{\partial t} = \begin{bmatrix} 4  &-3\\ 6 & -7\end{bmatrix}\mathbf{x} = \mathbf{Px}
$$
Conjecture Solutions:
$$
x_1(t) = \begin{bmatrix} 3e^{2t}\\ 2e^{2t}\end{bmatrix}  \text{ and }x_1(t) = \begin{bmatrix} e^{-5t}\\ 5e^{-5t}\end{bmatrix}
$$
Verify 
$$
\mathbf{Px}_1 = \begin{bmatrix} 6e^{2t}\\ 4e^{2t}\end{bmatrix} = 2\begin{bmatrix} 3e^{2t}\\ 2e^{2t}\end{bmatrix} = x_1'
$$

$$
\mathbf{Px}_2 = \begin{bmatrix} -5e^{-5t}\\ -15e^{-5t}\end{bmatrix} = x_2'
$$

How do we find solutions generally?

$\frac{\partial x}{\partial t} = P(t)\mathbf{x}$ is a homogenous equation

It should be a linear combination of $n$ independent solutions $x_1,…x_n$ by principle of superpostion 
$$
x(t) = c_1X_1(t) + c_2x_2(t) \\
= c_1  \begin{bmatrix} 3e^{2t}\\ 2e^{2t}\end{bmatrix} + c_2\begin{bmatrix} -e^{-5t}\\3e^{-5t}\end{bmatrix} \\
= 2  \begin{bmatrix} 3e^{2t}\\ 2e^{2t}\end{bmatrix} + 3 \begin{bmatrix} -e^{-5t}\\3e^{-5t}\end{bmatrix} 
$$
Consider constant-coefficient setting, use eigenvalue methode to get solutions 

We know the solutions will be the sum of linearly independent solutions $x_1,…x_n$

Seems reasolable to expect:
$$
\mathbf{x}(t) = \mathbf{v}e^{\lambda t}
$$


Because 
$$
x_i(t) = v_ie^{\lambda t} \text{ and } x_i'(t) = \lambda v_ie^{\lambda t}
$$


Note $e^{\lambda t}$ cancels everywhere, hence $\mathbf{x} = A\mathbf{x}$, trial solution $\mathbf{x} = \mathbf{v}e^{\lambda t} \text{ and } \mathbf{x}' = \lambda \mathbf{v}e^{\lambda t}$ so we have the eigendecomposition 



To find solutions of $\mathbf{x}' = \mathbf{Ax}$

1. Find eigenvalues of **A**
2. try to find n linearly independent eigenvectors associated with eigenvalues (if not possible use Jordan or Schur decomposition)
3. If possible then we get $n$ linearly indepenent solutions 

## Linear Systems

An independent class of continuous time LTI systems are when the I/O statsify linear constant coefficient diff eqs.
$$
\sum_{k=0}^{N}a_k\frac{\partial^ky(t)}{\partial t^k} = \sum_{k=0}^{M}b_k\frac{\partial^kx(t)}{\partial t^k}
$$


How to find frequency response of LTI 

#### Approach 1

Use the fact complex exponentials are eigenfunctions of LTI systems. 

if $x(t) = e^{j\omega t}$, then  output is $y(t) = H(j\omega)e^{j\omega t}$

#### Approach 2

Use differential property of Fourier Transforms

LTI systems statistfy $Y(j\omega) = H(j\omega)X(j\omega)$ 

Consider Fourier transforms of differential equations
$$
\mathcal F \Big\{ \sum_{k=0}^{N}a_k\frac{\partial^ky(t)}{\partial t^k}\Big\} = \mathcal F \Big\{\sum_{k=0}^{M}b_k\frac{\partial^kx(t)}{\partial t^k} \Big\}
$$
By linearity 
$$
\sum_{k=0}^{N}a_k\mathcal F \Big\{ \frac{\partial^ky(t)}{\partial t^k}\Big\} = \sum_{k=0}^{M}b_k\mathcal F \Big\{ \frac{\partial^kx(t)}{\partial t^k} \Big\}\\
\sum_{k=0}^{N}a_k Y(j\omega) = \sum_{k=0}^{M}b_kX(j\omega)\\
\frac{Y(j\omega)}{X(j\omega)} = \frac{\sum_{k=0}^{N}a_k}{\sum_{k=0}^{M}b_k}
$$


## Discrite Time / Difference Equations

$Nth$ order linear constant-coeffienent differnece equation
$$
\sum_{k=0}^N a_ky[n-k] = \sum_{k=0}^M a_kx[n-k]
$$
$H(j\omega)$  is DTFT frequency response 

Here also complex exponetials $e^{j\omega n}$ are eigenfunctions of LTI systems
$$
x[n] = e^{j\omega n}, \text{then } y[n] = H(e^{j\omega})x[n] 
$$

$$
H(e^{j\omega}) = \frac{\sum_{k=0}^{M}b_ke^{-jk\omega}}{\sum_{k=0}^{N}a_ke^{-jk\omega}}
$$


$$
 
$$






