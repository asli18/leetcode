#### 7. Reverse Integer
Given a 32-bit signed integer, reverse digits of an integer.
<p align="center">
    <img src="https://github.com/asli18/leetcode/blob/master/007_example.png?raw=true" alt="007_example"/>
</p>

```c
#include <limits.h>

int reverse(int x) {
    long long int res = 0;


    while (x != 0) {
        res = (res * 10) + x % 10;
        x /= 10;
    }

    return ((res > INT_MAX) || (res < INT_MIN)) ? 0 : (int)res;
}
```
