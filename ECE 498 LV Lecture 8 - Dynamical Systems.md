# ECE 498 LV Lecture 8 - Dynamical Systems

Consider a deterministic, scalar system of a continuous-valued variable evolving in continuous time $t$

_Ex._ $x(t)$ evolves accoring to $\frac{\partial x}{\partial t} = f(x)$

We also have an initial condition $x_0$ taken by $x$ at time $t_0$

$\implies$ last time we saw examples where $f( )$ was linear

An example of nonlinear dynamical system (modeling infections) where $x$ is fraction of infected individuals
$$
\frac{\partial x}{\partial t} = \beta x(1-x)
$$
One can also consider dynamical systems of serveral variables (nodes of network)
$$
\frac{\partial x}{\partial t} = f(x,y)\\
\frac{\partial y}{\partial t} = g(x,y)
$$
Can also have time varying
$$
\frac{\partial x}{\partial t} = f(x,t)
$$


Introduce $y=t$
$$
\frac{\partial x}{\partial t} = f(x,y)\\
\frac{\partial y}{\partial t} = 1\\
y(0)= 0
$$
Formally don't need time-varying systems, sunce we can always augment statespace 

##  

#####  Another genralization:

Systems governed by higher order derivatives 
$$
\frac{\partial ^2 x}{\partial t^2} + \Big(\frac{\partial x}{\partial t}\Big)^2 - \frac{\partial x}{\partial t}= f(x)
$$
Introduce $y= \frac{\partial x}{\partial t}$ then 
$$
y= \frac{\partial x}{\partial t}, \frac{\partial y}{\partial t}  =  f(x) - y^2 +y
$$
Focus of first-order dynamics that are not time varying 

Simple one-variable dynamics can always be solved in principle 
$$
\frac{\partial x}{\partial t}= f(x)\\
\int_{x_0}^{x} \frac{\partial x'}{f(x')} = t - t_0
$$
"Solving" means going from an implict characterization of system state to an explicity one 



For two or  more variables, not generally possible to find a solution (networks with many variables)

## Fixed Point Analysis 

A **fixed point** is steady-state value of system, so it remains stationary 

Fixed point $x=x^*$ is s.t $f(x^*) = 0$ or $\frac{\partial x}{\partial t} = 0$

for 2 variable systems fixed point is a pair $(x^* , y^*)$ i.e. $\frac{\partial y}{\partial t} = \frac{\partial x}{\partial t} = 0$

Dynamics easier to understand need fixed points 
$$
x = x^* + \epsilon\\
\frac{\partial x}{\partial t}= \frac{\partial x^*}{\partial t} + \frac{\partial \epsilon}{\partial t} \\
\frac{\partial x}{\partial t} = \frac{\partial \epsilon}{\partial t} = f(x^*+\epsilon)
$$


Taylor expansion about $x=x^*$ 
$$
\frac{\partial \epsilon}{\partial t}  = f(x^*) + \epsilon f'(x^*) + 0(\epsilon^2)\\
= \epsilon f'(x^*)
$$






where $f'()$ is derivative neglecting high order term
$$
\frac{\partial \epsilon}{\partial t} = \epsilon f'(x^*)
$$


First order **linear** diff eq
$$
\epsilon(t) = \epsilon(0)e^{\lambda t}\\
\text{where } \lambda = f'(x^*)
$$


depending on sign of $\lambda$, distance $\epsilon$ from fixed point, will either grow or decay exponentially over time 

$\implies$ **Linear stability analysis**

- $\lambda < 0$:
  - Attracting fixed points i.e. for where points close to fixed-point are artracted
- $\lambda > 0$ :
  - Repelling fixed points 
- $\lambda = 0$ 
  - Either attracting or repelling based on higher order terms (or other weird stuff)

## Extended Linear Stability Analysis 

$(x*,y*)$ where $f(x^*, y^*) = 0$ and $g(x^*, y^*) = 0$ consider nearby $x = x* + \epsilon$, $y = y* + \epsilon$
$$
\frac{\partial x}{\partial t} = \frac{\partial \epsilon_ x}{\partial t} = f(x^* + \epsilon, y^* + \epsilon) \\
= f(x^*,y^*) + \epsilon_xf^{(x)}(x^*,y^*) +  \epsilon_yf^{(y)}(x^*,y^*) +  ...\\
=  \epsilon_xf^{(x)}(x^*,y^*) +  \epsilon_yf^{(y)}(x^*,y^*)\\
$$

$$
\frac{\partial \epsilon_ x}{\partial t} = \epsilon_xf^{(x)}(x^*,y^*) +  \epsilon_yf^{(y)}(x^*,y^*)\\
\frac{\partial \epsilon_ x}{\partial t} = \epsilon_xg^{(x)}(x^*,y^*) +  \epsilon_yg^{(y)}(x^*,y^*)\\
$$

Suppose $J$ was diagonal
$$
\begin{bmatrix}
\frac{\partial \epsilon_ x}{\partial t} \\
\frac{\partial \epsilon_ y}{\partial t}
\end{bmatrix}
=
\begin{bmatrix}
\lambda_1 && 0 \\
0 && \lambda_2
\end{bmatrix}
\begin{bmatrix}
\epsilon_ x\\
\epsilon_ y
\end{bmatrix}
$$
If $\lambda_1, \lambda_2$ are real numbers, then equations for $\epsilon_ x, \epsilon_ y$ are decoupled
$$
\frac{\partial \epsilon_ x}{\partial t} = \lambda_1\epsilon_x \implies \epsilon_x(t) = \epsilon_x(0) e^{\lambda_1 t} \implies x(t) = x^* + \epsilon_xe^{\lambda_1 t} \\
\frac{\partial \epsilon_ x}{\partial t} = \lambda_2\epsilon_y \implies \epsilon_y(t) = \epsilon_y(0) e^{\lambda_2 t} \implies y(t) = y^* + \epsilon_ye^{\lambda_2 t} \\
$$


So $x$ and $y$ are independently attracting / repelling depending on the sign of $\lambda_{1}, \lambda_2$ 

- If both negative:
  - Attracting
- if both positive 
  - repelling 
- if different 
  - saddle point



What if $J$ is not diagonal? Find combinations of variables $x$ and $y$ that do move independently 
$$
z_1 = a\epsilon_x + b\epsilon_y\\
z_2 = c\epsilon_x + d\epsilon_y\\
z =\mathbf{Q\epsilon}\\
\frac{\partial z}{\partial t} = \mathbf{Q}\frac{\partial \epsilon}{\partial t} = \mathbf{QJ\epsilon} = \mathbf{QJQ^{-1}z}
$$


If $z_1, z_2$ to evolve independently $\mathbf{QJQ^{-1}}$ to be diagonal, $\mathbf{Q}$ should be matrix of eigenvectors of $\mathbf{J}$
$$
\frac{\partial z_1}{\partial t} = \lambda_1z_1\\
\frac{\partial z_2}{\partial t} = \lambda_1z_2\\
z_1(t) = z_1(0)  e^{\lambda_1 t} \\
z_2(t) = z_2(0)  e^{\lambda_2 t}
$$
The  eigenvector axes, play the role of attractor/repulser in phase space

If eigenvalues are complex $\rightarrow$ oscillation. spirals in phase space

In addition to fixed points, also possible to have *limit cycles*, (stable oscillatory behavior )

**Strange attractors** have a fractal structure 



