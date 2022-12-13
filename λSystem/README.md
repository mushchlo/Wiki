# Huh?
This is an exploratory programming language / OS for my own curiosity. It came together after a realization that [[E-Graphs]] could be used to represent expressions mid-execution, which felt like a native way to provide what untyped lambda calculus expects, while allowing the *currently loaded source* to be optimized on-the-fly to another form, thanks to the power of e-graphs, with arbitrary optimization functions. It also allowed for heaped objects for free, so it felt like a very native way to represent lambda programs as numbers.

# Why?
Well it's cool! Basically, this gives you one simple system that simultaneously does the following:
 - Compression of programs for free (many useful expressions can fit into a single register)
 - Generational cost minimization, with arbitrary cost models. (You can choose what you want to avoid, and it gets better at that across updates).
 - Possibly automatic parallelization.
 - Highly expressive and compact AST.

# Background
This project is based on an encoding of [[λ calculus]] called Blc, which was made by John Tromp
 - `Binary Lambda Calculus and Combinatory Logic, in Randomness And Complexity, from Leibniz To Chaitin_, ed. Cristian S. Calude, World Scientific Publishing Company, October 2008, pages 237-260 (The last reference, to an initial Haskell implementation, is dated 2004)` [(pdf version)](http://tromp.github.io/cl/LC.pdf)
If you have not seen this before, it would be helpful to familiarize yourself with it.


# Spec
[[Spec]]


# Syntax
 - λSystem is a language based on Blc, an encoding made by John Tromp.
	 - Source: 
 - The structure of an eggBlc program is simply a list of expressions represented as e-graphs; E-Graphs were invented as part of (Gregory Nelson’s [PhD Thesis](https://courses.cs.washington.edu/courses/cse599f/06sp/papers/NelsonThesis.pdf), 1980).
### Example Expression
This is the expression we will use as an example for converting between forms: the Z combinator. $$Z = \lambda g \rightarrow (\lambda x \rightarrow g \space(\lambda v \rightarrow x \space x \space v)) \space (\lambda x \rightarrow g \space (\lambda v \rightarrow x \space x \space v))$$.
This expression is written with Debrujin naming like so: $\lambda (\lambda1 (\lambda110)) (\lambda1 (\lambda110))$
- Parameters are referenced as $n$, definitions are referenced as $\$n$, and literal numbers are represented as `n`. 
- Sorted by  $(R * s)$, with R = reference count and s = size in the definition table.
- $capture \space n$ gets the variable that is named $n+1$ once the expression is fully applied
	- It's a way to get argument captures for quite cheap.
	- Uses [[λ prefix number]]
| #   | size | references | S\*r | λ-calculus w/ Debrujin                                                 | Blc Encoding               |
| --- | ---- | ---------- | ---- | ---------------------------------------------------------------------- | -------------------------- |
| 1   |      |            |      | capture 1                                                              |                            |
| 2   |      |            |      | $\lambda (capture \space 0) \space \#3$                                | 00 01 (01 #0 10) (00 )     |
| 3   |      |            |      | $\lambda \space \#1 \space \#1$                                        | 00 01 #1 #1                |
| 4   |      |            |      | $\lambda \space (capture \space 1) \space (capture \space 1) \space 0$ | 00 (01 #0 110) (01 #0 110) |

<!-- TBLFM: @1$1..@>$1=(@-1+1) -->

# Source
An example program to convert to and from eggBlc is provided [here](https://github.com/mushchlo/eggBlc)


# Preface, assumptions
* For the order notation where complexity is analyzed, I assume that eggBlc is being evaluated on a machine with $T$ threads capable of basic arithmetic operations and the addressing of memory provided to them (for example as a shader when using graphics cards for parallel compute). This allows all T threads to participate in the parsing of 
* The array of bytes underlying the heap is exposed to us as $B$, and the $ith$ byte o f $B$ is $B_i$.

# Algorithm to apply functions
1. Let $w_{sector} = len(B) / T$
2. Let 
3. $\forall i \in B :$  