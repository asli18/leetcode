#### 8. String to Integer (atoi)
Implement `atoi` which converts a string to an integer.

The function first discards as many whitespace characters as necessary until the first non-whitespace character is found. Then, starting from this character, takes an optional initial `plus or minus` sign followed by as many numerical digits as possible, and interprets them as a numerical value.

The string can contain additional characters after those that form the integral number, which are ignored and have no effect on the behavior of this function.

If the first sequence of non-whitespace characters in `str` is not a valid integral number, or if no such sequence exists because either `str` is empty or it contains only whitespace characters, no conversion is performed.

If no valid conversion could be performed, a zero value is returned.

<p align="center">
    <img src="https://github.com/asli18/leetcode/blob/master/008_example.png?raw=true" alt="008_example"/>
</p>

- 先判斷是否有空白, '-' or '+', 其他除了數字以外的都是無效字元，返回 0
- 每次累加確定是否已經溢位
- 負值取2的補數
<div style="page-break-after: always;"></div>

```c
int myAtoi(char *str)
{
    bool neg = 0;
    long long int res = 0;

    while (*str == ' ')
        str += 1;

    if (*str == '-') {
        neg = 1;
        str += 1;
    } else if (*str == '+') {
        str += 1;
    }

    while (*str != 0) {
        if ((*str > '9') || (*str < '0'))
            break;

        if ((res = ((res * 10) + (*str++ - '0'))) > INT_MAX)
            return (neg) ? INT_MIN : INT_MAX;
    }

    return (neg) ? (~res + 1) : res;
}
```
