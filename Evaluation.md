
# Definition
	The reduction of a [[λ calculus]] expression $e$ into a normal form.

All applications where
$$e = apply \space (\lambda v . e_1) \space e_2$$
are subject to the transformation
$$e = substitute(e_1, v, e_2)$$
where $substitute(e_1, v, e_2)$ is a function that replaces all instances of the literal string $v$ within $e_1$ with the expression $e_2$.

#todo