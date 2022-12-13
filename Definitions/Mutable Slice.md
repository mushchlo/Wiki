A "mutable slice" of memory is a segment of memory on which 3 methods are provided:
1. An $O(1)$ function `get : (Slice, index: u64) -> u8`
3. An $O(1)$ function `len : Slice -> u64`
2. An $O(1)$ function `set : (Slice, index: u64, val: u8) -> Slice`[^1]

[^1]: It is guaranteed that after calling this function, the Slice passed in will not be used again