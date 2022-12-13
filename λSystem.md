# Huh?
This is an exploratory programming language / OS for my own curiosity. It came together after a realization that [[Jot]] would make for a relatively easy way of encoding lambdas as numbers, described at [[λs as numbers]].

# Why?
Well it's cool! Basically, this gives you one simple system that simultaneously does the following:
 - Compression of programs for free (many useful expressions can fit into a single register)
 - Generational cost minimization, with arbitrary cost models. (You can choose what you want to avoid, and it gets better at that across updates)
 - Possibly automatic parallelization
 - Highly expressive AST despite it's size

# Background
This project is based on an encoding of [[λ calculus]] called [Blc](https://tromp.github.io/cl/Binary_lambda_calculus.html), which was made by John Tromp
 - `Binary Lambda Calculus and Combinatory Logic, in Randomness And Complexity, from Leibniz To Chaitin_, ed. Cristian S. Calude, World Scientific Publishing Company, October 2008, pages 237-260 (The last reference, to an initial Haskell implementation, is dated 2004)` [(pdf version)](http://tromp.github.io/cl/LC.pdf)
If you have not seen this before, it would be helpful to familiarize yourself with it.


# Spec
[[Spec]]


# Syntax
 - λSystem is a language based on Blc, an encoding made by John Tromp.
	 - Source: 
 - The structure of an eggBlc program is simply a list of expressions represented as e-graphs; E-Graphs were invented as part of (Gregory Nelson’s [PhD Thesis](https://courses.cs.washington.edu/courses/cse599f/06sp/papers/NelsonThesis.pdf), 1980).
### Example Expression
This is the expression we will use as an example for converting between forms: the Z combinator. $$Z = \lambda g \rightarrow (\lambda x \rightarrow g \space(\lambda v \rightarrow x \space x \space v)) \space (\lambda x \rightarrow g \space (\lambda v \rightarrow x \space x \space v))$$

# Preface, assumptions
* For the order notation where complexity is analyzed, I assume that eggBlc is being evaluated on a machine with $T$ threads capable of basic arithmetic operations and the addressing of memory provided to them (for example as a shader when using graphics cards for parallel compute). This allows all T threads to participate in the parsing of 
* The array of bytes underlying the heap is exposed to us as $B$, and the $ith$ byte o f $B$ is $B_i$.




