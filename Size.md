The size of a Jot program of length L in bitstring form is given by
$$\begin{align}
size \space [] &= 1\\
size \space b:B &= lzcnt(num \space (b:B))
\end{align}$$
... where $b$ is a boolean, $B$ is a bitstring, $[]$ is the empty bitstring, and $b:B$ is the list beginning with $b$, with the rest of the lest being $B$.

The function $num$ gives you the numeric representation of a bitstring, which is as follows.

(using [[../../λs as numbers |λs as numbers]])
$$\begin{align}\\
num \space [] &= 0\\
num \space (bit:B) &= (bit << 1) + 1 + num(B)
\end{align}$$
where
$$num \space B = (make\_num \space (1:B)) - 1$$
where make_num just interprets the bits of a bitstring as though it were a number, and therefore has the definition

```
// The following program in Haskell can make any bitstring that provides
// indexing (starting from 0) into a number.
// This includes numerically encoded bitstrings.

// This program is parallel by default. If you want to run this sequentially
// (because you don't care about speed, or you don't have any sort of
// parallelization at all, etc.) you can replace 'parallel_map' and
// 'parallel_reduce' with their sequential equivalents ('map' and 'reduce').

parallel_reduce :: Array a -> (a -> a -> a) -> a
parallel_reduce a f =
	
	let to_run = (f (a b))
	parallel_reduce (to_run)


all_zeroes B =
	parallel_reduce bits (&&)
-- Runtime with b bits, t threads and a highest 1-bit index of i
-- (where index 0 is the least significant bit):
--------------------- O((b - i) / t) ---------------------
-- This runtime is guaranteed to be constant when 64 or more threads are
-- available.

make_num B =
	if (all_zeroes B) then
		return 0
	
	// cannot be negative, as (make_num B) > 0
	first_one_idx = 63 - lzcnt(n)

	// if the first 1-bit is the first (least significant) bit,
	// then the number is 1.
	if first_one_idx == 0 then
		1
	else
		res = 0
		parallel_for i in first_one_idx..64
			if B[i] then
				res |= 1 << i
```




$$\begin{align}
make\_num \space [] &= 0\\
make\_num \space 0:B &= make\_num \space B\\
make\_num \space 1:B &= (2 * (make\_num \space B)) + 1
\end{align}$$
Calling this function with $[100]$ gives the result
$$\begin{align}
make\_num \space [100] &= 1:[00]\\
make\_num \space [100] &= (2^1 * (make\_num \space [00])) + 1\\
make\_num \space [100] &= (2^2 * (make\_num \space [0])) + 1\\
make\_num \space [100] &= (2^2 * (make\_num \space [])) + 1\\
make\_num \space [100] &= (2 * 0) + 1
\end{align}$$
Which is as expected, as 01 re

#stub