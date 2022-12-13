λ-depth is a property of a λ-calculus expression, or of a specific context within a λ-calculus expression. It is computed as the number of lambdas preceding an expression, but it's properties are tied directly with the information contained in a λ-expression.

The number of λ's before a position in the source code, or the total deepest nesting of lambdas.

## Runtime:
$O(n)$ with no parallelism.
$O(n/t)$ with $t$ threads

# Expressions possible to create with N bits
These are written using [[../../Debrujin Indices]]

## N = 0
| Desired numeric representation | λ-Expression | # in depth |
| ------------------------------ | ------------ | ---------- |
| 0                              | λ0           | 0          |
| 1                              | λ00          | 0          |
| 2                              | λλ01         | 1          |
| 3                              | λλ10         | 2          |
| 4                              | λλ11         | 3          |
| 5                              | λλλ0(12)     | 0          |
| 6                              | λλλ(01)2     | 1          |
| 7                              | λλλ0(21)     | 2          |
| 8                              | λλλ(02)1     | 3          |
| 9                              | λλλ1(02)     | 4          |
| 10                             | λλλ1(20)     | 5          |
| 11                             | λλλ(12)0     | 6           |
<!-- TBLFM: @3$1..@>$1=(@-1+1) -->

Number of individual programs at only depth $D$ is $$count \space D = \displaystyle\sum_{i=1} ^{D} {\displaystyle i \choose D}$$
The first program of depth $D$ is$$prog_{0} \space D = \displaystyle\sum_{i=1} ^{D-1} {count \space (i-1)}$$
The $ith$ program of depth $D$ is then$$(count(D-1) <<$$

#todo