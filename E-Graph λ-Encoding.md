
# Encoding

The following encoding is based on [[Counting the functions]]. We take an arbitrary number, convert it to a bitstring, and evaluate the Jot program represented by that bitstring.

| Number (decimal) | Number (binary) | Bitstring | Program   |
| ---------------- | --------------- | --------- | --------- |
| 0                | 0               | ""        | I         |
| 1                | 1               | "0"       | S (K "")  |
| 2                | 10              | "1"       | ("" S) K  |
| 3                | 11              | "00"      | S (K "0") |
| 4                | 100             | "01"      | ("1" S) K |
| 5                | 101             | "10"      | ("0" S) K |
| 6                | 110             | "11"      |           |
where "n" means 'translation of bitstring n'

