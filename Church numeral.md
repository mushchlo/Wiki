A common encoding of the natural numbers ($\mathbb{N}$) in [[λ calculus]].

$$\begin{align}
0 &= \lambda f . \lambda x . x = \lambda \lambda 0\\
1 &= \lambda f . \lambda x . f \space x = \lambda \lambda 10\\
n+1 &= \lambda n . \lambda f . \lambda x . f \space (n \space f \space x) = \lambda \lambda 1(210)\\
\end{align}$$
#stub