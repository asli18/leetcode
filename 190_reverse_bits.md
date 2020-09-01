#### 190. Reverse Bits
Reverse bits of a given 32 bits unsigned integer.
<p align="center">
    <img src="https://github.com/asli18/leetcode/blob/master/190_example.png?raw=true" alt="190_example"/>
</p>
- 先右移到 bit 0 再左移到目標bit
```c
uint32_t reverseBits(uint32_t n) {
    uint32_t res = 0;
    
    for (uint32_t i = 0; i < 32; ++i)
        res |= (((n & (1u << i)) >> i) << (31u - i));
    return res;
}
```

