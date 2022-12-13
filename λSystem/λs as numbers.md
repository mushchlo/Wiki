## Definitions

A *bitstring* is defined as a string of bits of constant length. All that is required is to be able to index the bits, in some fashion. Bitstrings can either be empty, or a bit before/after a bitstring.
$$[01] = 0:[1] = 0:(1:[])$$
In order to map bitstrings to the natural numbers (to get a binary encoding of bitstrings), we will require a dummy bit that is always 1 to precede a bitstring encoded as a binary number. That means that in binary, the encoded value will always start with a 1, and the bitstring is whatever bits come after that 1. Therefore...
| input (bitstring) | Output (binary) | Output (decimal) |
| ----------------- | --------------- | ---------------- |
| []                | 1               | 1                |
| [0]               | 10              | 2                |
| [1]               | 11              | 3                |
| [00]              | 100             | 4                |
| [01]              | 101             | 5                |
| [10]              | 110             | 6                |
| [11]              | 111             | 7                |
| [000]             | 1000            | 8                |
| [001]             | 1001            | 9                |
| [010]             | 1010            | 10               |
| [011]             | 1011            | 11               |
| [100]             | 1100            | 12               |
| [101]             | 1101            | 13               |
| [110]             | 1110            | 14               |
| [111]             | 1111            | 15               |

However, this can be reduced further, to a 1:1 encoding with the naturals. This is done by subtracting the output numbers by one.
| Input (bitstring) | Output (binary) | Output (decimal) |
| ----------------- | --------------- | ---------------- |
| []                | 0               | 0                |
| [0]               | 1               | 1                |
| [1]               | 10              | 2                |
| [00]              | 11              | 3                |
| [01]              | 100             | 4                |
| [10]              | 101             | 5                |
| [11]              | 110             | 6                |
| [000]             | 111             | 7                |
| [001]             | 1000            | 8                |
| [010]             | 1001            | 9                |
| [011]             | 1010            | 10               |
| [100]             | 1011            | 11               |
| [101]             | 1100            | 12               |
| [110]             | 1101            | 13               |
| [111]             | 1110            | 14               |
| [0000]            | 1111            | 15               |

# Decoding
Therefore, to make any 64-bit number (*of constant size*, this ISNT a variable length encoding) into a binary string, add 1 to it, then read all of the bits past the first one.
| Input (decimal) | Input (binary) | Output (binary) | Equivalent bitstring |
| --------------- | -------------- | --------------- | -------------------- |
| 0               | 0              | 1               | ""                   |
| 1               | 1              | 10              | "0"                  |
| 2               | 10             | 11              | "1"                  |
| 3               | 11             | 100             | "00"                 |
| 4               | 100            | 101             | "01"                 |
| 5               | 101            | 110             | "10"                 |
| 6               | 110            | 111             | "11"                 |
| 7               | 111            | 1000            | "000"                |
| 8               | 1000           | 1001            | "001"                |
| 9               | 1001           | 1010            | "010"                |
| 10              | 1010           | 1011            | "011"                |
| 11              | 1011           | 1100            | "100"                |
| 12              | 1100           | 1101            | "101"                |
| 13              | 1101           | 1110            | "110"                |
| 14              | 1110           | 1111            | "111"                |


## Encoding of functions
We use the language [Jot](https://esolangs.org/wiki/Jot) to encode programs as bitstrings, which allows for, in combination with the encoding above, a natural numeric encoding of abitrary programs written in [[../Jot/Jot|Jot]], or equivalently [[SKI calculus]], or equivalently [[../λ-calculus/λ calculus|λ calculus]].

# Algorithms
To encode a number n as a (numeric) bitstring:
$bitstring(n) = a + 1$

Because right-shifting a numeric bitstring by one (diving it by two) and adding one gives the tail of a bitstring, this can be very fast.

$$\begin{align}
tail(0) &= 0\\
tail(n) &= \{\\
&       first\_1\_idx = 64-leading\_zeroes(n)\\
&             hi
\\\}

\end{align}$$
(this assumes that n is encoded as a bitstring (greater than 0))


To evaluate a number $n$ as a Jot program, call $Jot(n)$.  
$$\begin{align}
Jot(0) &= I\\
Jot(n) &= Jot\_aux(n-1)\\
\\
Jot\_aux(n) &=
\end{align}$$
$0$ and $1$ both take in numeric bitstrings, and have the following definitions:

#todo