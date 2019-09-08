---
title: Dinatural transformations
preamble: \usepackage{tikz-cd}\usetikzlibrary{cd}\usepackage{xcolor}

---

# Dinatural transformations

*Assumptions: categories, functors, natural transformations, functor categories*

I'll describe how you can arrive at the defintion of a dinatural transformation yourself.

Recall that a natural transformation is a map $\alpha: F \Rightarrow G$ between two functors with the same domain and codomain

$$
\begin{tikzcd}[column sep=large] C \ar[r, bend left=18pt, "H"]\ar[r, bend right=18pt, "G"']\ar[r, phantom, "\scriptstyle\alpha\!\Downarrow\;"]& D \\
\\
\end{tikzcd}
$$

These domain and codomain can be any categories - and in this case we are going to consider the case when the domain is the product category $\mathcal{C}^{op} \times C$.

Observe that


Let's first analyze how functors whose domain is a product category behave.
Since, for any morphism $f: A \rightarrow B$ in the original category $\mathcal{C}$, the following square in the _product category_ $\mathcal{C}^{op} \times \mathcal{C}$ has to commute:

$$
\begin{tikzcd}
&       B \times A \ar[rr, "1_A \times f"] &           &  B \times B\\
A \times A \ar[ru, "f \times 1_A"] \ar[rrru] \ar[rr, "1_A \times f"'] && A \times B \ar[ru, "f \times 1_B"']  & \\
& A\\
\end{tikzcd}
$$

this means the functor has to preserve the commutativity of this square:

$$
\begin{tikzcd}
&       F(B \times A) \ar[rr, "F(1_A \times f)"] &           &  F(B \times B)\\
F(A \times A) \ar[ru, "F(f \times 1_A)"] \ar[rrru] \ar[rr, "F(1_A \times f)"'] && F(A \times B) \ar[ru, "F(f \times 1_B)"']  & \\
& A\\
\end{tikzcd}
$$

Why are we talking about this? It will become apparent once we study a natural transformation $\alpha: F \Rightarrow G$.
Recall that a natural transformation $$ \begin{tikzcd}[column sep=large] \mathcal{C} \ar[r, bend left=18pt, "H"]\ar[r, bend right=18pt, "G"']\ar[r, phantom, "\scriptstyle\alpha\!\Downarrow\;"]& \mathcal{D} \\ \\ \end{tikzcd} $$ to every object $A$ in $\mathcal{C}$ assigns a morphism $\alpha_A: F(A) \rightarrow G(A)$ such that the following square commutes:


$$
\begin{tikzcd}
F(A) \ar[r, "F(f)"] \ar[d, "\alpha_A"]  & F(B) \ar[d, "\alpha_B"]\\
G(A)    \ar[r, "f"]                     & G(B)    \\
& A\\
\end{tikzcd}
$$

Now,  the power of category theory is that it allows us to get rid of [leaky abstractions](https://www.joelonsoftware.com/2002/11/11/the-law-of-leaky-abstractions/). For example, if we want to define a natural transformations, to define it we will never need something more than a specific morphism for every object such that the naturality condition is satisfied. We neve

Once we lower the level of abstraction and consider the actual product category underneath we get the following commutative diagram:

$$
\begin{tikzcd}
&       F(B \times A) \ar[dddd, red, "\alpha_{B \times A}"] \ar[rr, "F(1_A \times f)"] &           &  F(B \times B) \ar[dddd, red, "\alpha_{B \times B}"]\\
F(A \times A) \ar[dddd, red, "\alpha_{A \times A}"] \ar[ru, "F(f \times 1_A)"] \ar[rr, "F(1_A \times f)"'] && F(A \times B) \ar[dddd, red, "\alpha_{A \times B}"]\ar[ru, "F(f \times 1_B)"']  & \\
& & & & &\\
& & & & &\\
&       G(B \times A) \ar[rr, "G(1_A \times f)"] &           &  G(B \times B)\\
G(A \times A) \ar[ru, "G(f \times 1_A)"]  \ar[rr, "G(1_A \times f)"'] && G(A \times B) \ar[ru, "G(f \times 1_B)"']  & \\
& A\\
& A\\
& A\\
& A\\
& A\\
\end{tikzcd}
$$

Observe that this is a quite strong. We can weaken the constraints such that we end up with a more general construction.
Namely, we can require that the construction only needs to satisfy the following commuting cube:

$$
\begin{tikzcd}
&       F(B \times A) \ar[rr, "F(1_A \times f)"] &           &  F(B \times B) \ar[dddd, red, "\alpha_{B}"]\\
F(A \times A) \ar[dddd, red, "\alpha_{A}"] \ar[ru, "F(f \times 1_A)"] \ar[rr, "F(1_A \times f)"'] && F(A \times B) \ar[ru, "F(f \times 1_B)"']  & \\
& & & & &\\
& & & & &\\
&       G(B \times A) \ar[rr, "G(1_A \times f)"] &           &  G(B \times B)\\
G(A \times A) \ar[ru, "G(f \times 1_A)"]  \ar[rr, "G(1_A \times f)"'] && G(A \times B) \ar[ru, "G(f \times 1_B)"']  & \\
& A\\
& A\\
& A\\
& A\\
& A\\
\end{tikzcd}
$$

Note what happened. We lose some morphisms and we renamed $\alpha_{A \times A}$ to $\alpha_A$. We only care about diagonal morphisms.
This is only possible when the domain category is $\mathcal{C}^op \times \mathcal{C}$.
That is, we defined something called a _dinatural_ transformation between two profunctors.

Flip some morphisms.


$$
\begin{tikzcd}
&       F(B \times A) \ar[rr, "F(1_A \times f)"] \ar[ld, "F(f \times 1_A)"'] &           &  \ar[dl, "F(f \times 1_B)"] F(B \times B) \ar[dddd, red, "\alpha_{B}"]\\
F(A \times A) \ar[dddd, red, "\alpha_{A}"]  \ar[rr, "F(1_A \times f)"'] && F(A \times B)   & \\
& & & & &\\
& & & & &\\
&       G(B \times A) \ar[dl, "G(f \times 1_A)"'] \ar[rr, "G(1_A \times f)"] &           &  G(B \times B) \ar[dl, "G(f \times 1_B)"]\\
G(A \times A)   \ar[rr, "G(1_A \times f)"'] && G(A \times B)   & \\
& A\\
& A\\
& A\\
& A\\
& A\\
\end{tikzcd}
$$

This commutation condition now has some loose ends. Since one of the categories is the opposite category $\mathcal{C}^{op}$ some of the morphisms turn out to be parts of paths where there isn't really a new choice added by the addition of $\alpha$ morphisms (colored blue).

$$
\begin{tikzcd}
&       F(B \times A) \ar[rr, "F(1_A \times f)"] \ar[ld, "F(f \times 1_A)"'] &           &  \ar[dl, "F(f \times 1_B)", blue] F(B \times B) \ar[dddd, red, "\alpha_{B}"]\\
F(A \times A) \ar[dddd, red, "\alpha_{A}"]  \ar[rr, "F(1_A \times f)"', blue] && \color{blue}{F(A \times B)}   & \\
& & & & &\\
& & & & &\\
&       \color{blue}{G(B \times A)} \ar[dl, "G(f \times 1_A)"', blue] \ar[rr, "G(1_A \times f)", blue] &           &  G(B \times B) \ar[dl, "G(f \times 1_B)"]\\
G(A \times A)   \ar[rr, "G(1_A \times f)"'] && G(A \times B)   & \\
& A\\
& A\\
& A\\
& A\\
& A\\
\end{tikzcd}
$$

After removing them, we end up with the usual hexagon diagram found as found on [Wikipedia](https://en.wikipedia.org/wiki/Dinatural_transformation).

$$
\begin{tikzcd}
&       F(B \times A) \ar[rr, "F(1_A \times f)"] \ar[ld, "F(f \times 1_A)"'] &           &   F(B \times B) \ar[dddd, red, "\alpha_{B}"]\\
F(A \times A) \ar[dddd, red, "\alpha_{A}"]  &&   & \\
& & & & &\\
& & & & &\\
&   &           &  G(B \times B) \ar[dl, "G(f \times 1_B)"]\\
G(A \times A)   \ar[rr, "G(1_A \times f)"'] && G(A \times B)   & \\
& A\\
& A\\
& A\\
& A\\
& A\\
\end{tikzcd}
$$
