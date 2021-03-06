---
title: the jacobian matrix
date: 2016-03-27
---

# The Jacobian Matrix

In the [last post](2016-02-28-thetangentbundle.html), we defined the tangent bundle. 
We have finally developed enough machinery to start seriously doing calculus on 
manifolds. In this post, we shall define the derivative of a smooth map between 
manifolds and translate the [implicit function theorem](https://en.wikipedia.org/wiki/Implicit_function_theorem) into the language 
of differential geometry. 

### Pulling back vector bundles

Suppose that $f : X \to Y$ is a smooth map between manifolds and $E$ is a vector 
bundle on $Y$. Then we can construct the pullback vector bundle $f^*E$ on $X$. The 
fiber over $x \in X$ is $(f^*E)_x = E_{f(x)}$. This describes $f^*E$ as a set. If 
$(\phi_{\beta\alpha})$ is gluing data for $E$, then $(\phi_{\beta\alpha} \circ f)$ is 
gluing data for $f^*E$. This describes $f^* E$ as a vector bundle. We can also realize 
the pullback bundle $f^*E$ as the following [fibered 
product](https://en.wikipedia.org/wiki/Pullback_%28category_theory%29):
$$\require{AMScd}
\begin{CD}
f^* E @>>> E;\\
@VVV @V{\pi}VV \\
X @>{f}>> Y;
\end{CD}$$
This universal property tells us how to define smooth maps into the vector bundle 
$f^*E$. Once we have developed more abstract sheaf theory, we will see a nice 
description for the sheaf of sections of $f^* E$, but we do not need it to talk about 
the Jacobian matrix.

### The derivative of a smooth map

Suppose that $f : X \to Y$ is a smooth map between manifolds and $D \in T_pX$ is a 
differential operator. Define $(f'D)(g) = D(g \circ f)$ where $g \in 
\mathscr{C}_{Y,f(p)}$. Then $f' D \in T_{f(p)}Y$. If we represent tangent vectors as 
equivalence classes of curves $[\gamma(t)]$, then $f'[\gamma(t)] = [f \circ 
\gamma(t)]$. The maps $f' : T_p X \to T_{f(p)}Y$ are linear and they assemble to form 
a vector bundle homomorphism $f' : TX \to f^* TY$ which is called the **derivative** 
of $f$. If $x_1,\dots,x_m$ are coordinates around $p$ and $y_1,\dots,y_n$ are 
coordinates around $f(p)$, then $f$ can be written in the form $y_i = 
f_i(x_1,\dots,x_m)$. This implies that
$$f' = \left( \frac{\partial f_i}{\partial x_j} \right)$$
with respect to the frames $(\partial / \partial x_j)$, $(\partial / \partial y_i)$ 
of $TX$ and $TY$ respectively. This is the the [Jacobian 
matrix](https://en.wikipedia.org/wiki/Jacobian_matrix_and_determinant). 

### The Inverse Function Theorem

Suppose that $f : X \to Y$ is a smooth map with derivative $f' : TX \to f^* TY$. The 
[inverse function theorem](https://en.wikipedia.org/wiki/Inverse_function_theorem) 
says that if $p \in X$ and $f'_p$ is an isomorphism, then there are neighborhoods $p 
\in U$ and $f(p) \in V$ such that $U \subseteq f^{-1}(V)$ and $f : U \to V$ is a 
diffeomorphism. The inverse function theorem is plausible: If you 
take $p \in X$ and start zooming in around $p$, the smooth map $f$ starts to look like 
the linear map $f'_p$. Once you have zoomed in to inspect an extremely small open 
neighborhood around $p$, $f$ and $f'_p$ are indistinguishable to the naked eye, so 
you expect $f$ to be invertible on this open neighborhood. 

Let\'s try and make this rigorous. Since $f'_p$ is invertible and the determinant not vanishing is an open 
condition, we can choose open neighborhoods $p \in U$ and $f(p) \in V$ such that 
$f(U) \subseteq V$ and $f' : TU \to f^*TV$ is an isomorphism. By shrinking these open 
neighborhoods, we can assume that $U = \mathbb{R}^d$, $V = \mathbb{R}^d$ and both 
$p,f(p)$ are equal to zero in their respective coordinate charts. Now $f$ is a 
smooth map $\mathbb{R}^d \to \mathbb{R}^d$ sending $0$ to $0$ and $f' : \mathbb{R}^d 
\to {\rm GL}_d(\mathbb{R})$. We want to construct a germ $g$ around $0 \in 
\mathbb{R}^d$ taking values in $\mathbb{R}^d$ such that

- $fg = gf = {\rm id}$
- $g' = (f')^{-1}$

in the stalk. This is an example of an **integrability problem**. Integrability 
problems are the heart of differential geometry and we will see many examples 
later. Proving the inverse function theorem is equivalent to solving this 
integrability problem. If you want to solve integrability problems, you need to use 
advanced tools from analysis. Many famous open problems in differential geometry can 
be translated into integrability problems (for example, the existence of a complex 
structure on the 6-sphere). 

### The Implicit Function Theorem

Let $f : X \to Y$ be a smooth map whose derivative has constant rank $r$. Fix $p \in 
X$. Choose coordinates $x_1,\dots,x_m$ on $p \in U$ and $y_1,\dots,y_n$ on $f(p) \in 
V$ such that $f(U) \subseteq V$ and 
$$A = \left( \frac{\partial f_i}{\partial x_j} \right)_{i,j = 1,\dots,r}$$ 
is invertible at $p$. Since invertibility is an open condition, we can shrink $U$ and 
$V$ so that the minor $A$ is invertible on all of $U$. Consider the map $\Phi : U \to 
\mathbb{R}^m$ defined by $\Phi = (f_1,\dots,f_r,x_{r+1},\dots,x_m)$. The derivative is 
given by
$$\Phi' = \begin{pmatrix} A & * \\ 0 & I \end{pmatrix}$$
By shrinking $U$, the inverse function theorem implies that $\Phi$ becomes a 
diffeomorphism onto its image, which implies that $f_1,\dots,f_r,x_{r+1},\dots,x_m$ 
are coordinates on $p \in U$. With respect to these new coordinates, $f$ is given by
$$
\begin{split}
&y_1 = f_1 \\
&y_2 = f_2 \\
&\cdots \\
&y_r = f_r \\
&y_{r+1} = g_{r+1}(f_1,\dots,f_r,x_{r+1},\dots,x_m) \\
&y_{r+2} = g_{r+2}(f_1,\dots,f_r,x_{r+1},\dots,x_m) \\
&\cdots \\
&y_{n} = g_{n}(f_1,\dots,f_r,x_{r+1},\dots,x_m) \\
\end{split}
$$
and the derivative is given by
$$f' = \begin{pmatrix} I & 0 \\ * & B \end{pmatrix}$$
Since $f'$ has constant rank $r$, the matrix $B$ must be zero, which implies that each 
$g_j$ does not depend on $x_{r+1},\dots,x_m$. Consider the map $\Psi : V \to 
\mathbb{R}^n$ defined by 
$$\Psi = 
(y_1,\dots,y_r,w_{r+1} = y_{r+1}-g_{r+1}(y_1,\dots,y_r),\dots,w_n = y_n-g_n(y_1,\dots,y_r)).$$
Its derivative is 
$$\Psi' = \begin{pmatrix} I & 0 \\ * & I \end{pmatrix}$$
which is invertible, therefore by shrinking $U$ and $V$, 
$y_1,\dots,y_r,w_{r+1},\dots,w_{n}$ is a coordinate chart on $V$. With respect to the 
coordinate chart $(f_1,\dots,f_r,x_{r+1},\dots,x_m)$ on $U$ and 
$(y_1,\dots,y_r,w_{r+1},\dots,w_n)$ on $V$, $f$ is given by the following linear map:
$$\begin{pmatrix} I & 0 \\ 0 & 0 \end{pmatrix}$$
This result is often called the implicit function theorem or the rank theorem. It 
tells us that $x_{r+1},\dots,x_m$ are coordinates around $p$ in $f^{-1}(f(p))$. The 
implicit function theorem is best demonstrated with a simple example: Consider the map 
$f : \mathbb{R}^2 \to \mathbb{R}$ defined by $f(x,y) = x^2 + y^2$. 
The derivative is given by 
$$f' = \begin{pmatrix} 2x & 2y \end{pmatrix}$$
which implies that $f : \mathbb{R}^2 \backslash \{ 0 \} \to \mathbb{R}$ has constant 
rank $1$. Consider the point $(1,0)$. The jacobian at this point is $\begin{pmatrix} 2 
& 0 \end{pmatrix}$. Therefore $y$ is a coordinate on $f^{-1}(1) = \{ (x,y) : x^2 + y^2 
= 1 \}$ in a neighborhood of $(1,0)$. This is easy to see geometrically:

![](/img/2016-03-27-implicitfunctionthmcoordinatechart.PNG)

Despite the simplicity of this example, it really captures what is going on. 
The implicit function theorem allows us to locally realize fibers of smooth maps as 
graphs. Similarly, $x$ is a coordinate on $\{ (x,y) : x^2 + y^2 = 1 \}$ in some 
neighborhood of $(0,1)$. These two coordinate charts intersect in the first quadrant and on the 
intersection, $y = \sqrt{1-x^2}$. 

A very similar argument proves that $x,y$ are coordinates around $(0,0,1)$ on the 
2-sphere $S^2 = \{ (x,y,z) : x^2 + y^2 + z^2 = 1 \}$.

![](/img/2016-03-27-spherenorthpolechart.PNG)

 Now consider the function $z : S^2 \to \mathbb{R}$ which gives the height above the $x,y$-plane. In a neighbourhood 
of $(0,0,1)$, we have $z = \sqrt{1-x^2-y^2}$. The derivative of $z$ is
$$z' = \left(\frac{-x}{\sqrt{1-x^2-y^2}},\frac{-y}{\sqrt{1-x^2-y^2}}\right)$$
Therefore, $z$ has rank $0$ at $(0,0,1)$ and rank $1$ in the rest of the neighborhood 
of $(0,0,1)$. Notice that $z^{-1}(1)$ is $0$-dimensional and $z^{-1}(1-\epsilon)$ is 
$1$ dimensional. This shows that the constant rank hypothesis we used to prove the 
implicit function theorem is necessary. 


### Exercises

- Let $A$ be a matrix. What is the jacobian of $x \mapsto Ax + b$?
- Using the implicit function theorem, carefully construct coordinates on $$S^n = \{ 
(x_0,x_1,\dots,x_n) : x_0^2 + \dots + x_n^2 = 1 \}$$
- when is the solution set of a polynomial $f(x_1,\dots,x_n)$ a smooth manifold?
- **(Harder)** Compute the Jacobian of the determinant map ${\rm det} : {\rm 
GL}_n(\mathbb{R}) \to \mathbb{R}^{\times}$.
