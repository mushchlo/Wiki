A [[../../λ calculus|λ calculus]] expression is "constant" if, when it [[../../Evaluation|is evaluated]], it remains the same.

Obviously, an expression with no applications is constant, so the programs $I = \lambda 0$, $K = \lambda \lambda 1$, and even $S = \lambda \lambda \lambda ((2 \space 0) \space (1 0))$ are all constant.

The famous Y combinator is therefore non-constant.
$$Y = (\lambda x . x \space x) \space (\lambda x . x \space x)$$
It's got an application right there! This expression therefore does not work in non-lazy evaluation contexts.

The less famous (but more useful!) Z combinator *is* constant:
$$Z = \lambda f . (
    (\lambda x . f \space (\lambda v . x \space x \space v)) (\lambda x . f \space (\lambda v . x \space x \space v))
)$$
Woah, thats a lot of nesting! Let's break it down into three definitions
$$\begin{align}
b &= \lambda x v.x \space x \space v \\
a &= \lambda f x.f \space (b \space x) \\
Z &= \lambda f. (a \space f) (a \space f) 
\end{align}$$
... and reduce them using De Brujin indices for variables
$$\begin{align}
b &= \lambda \lambda (1 \space 1 \space 0) \\
a &= \lambda \lambda (1 \space (b \space 0)) \\
Z &= \lambda ((a \space 0) \space (a \space 0))
\end{align}$$
Note that applying $Z \space f$ immediately invokes the expression
$$\begin{align}
Z &= (a \space f) \space (a \space f)\\
	&= (\lambda (f \space (b \space 0))) \space (\lambda (f \space (b \space 0)))
\end{align}$$
Which is another non-constant function! So, calling constant functions may result in a non-constant result.

#stub