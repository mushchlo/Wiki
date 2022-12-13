A slice of memory refers to a segment of memory on which 2 methods are provided:
1. An $O(1)$ function `get : (Slice, index: u64) -> u8`
2. An $O(1)$ function `len : Slice -> u64`