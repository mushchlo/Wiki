Assuming each binary number $b$ has $d$ digits followed by 1 newline ($d + 1$ total characters), how many characters does it take to print the binary numbers 0...N?

$$\displaystyle\sum_{i = 0} ^{N} {(width(i) + 1)}$$
where $$width(n) = (n=0) \space ? \space 1 : size(n) - lzcnt(n)$$
where $$size(n) = 64$$
