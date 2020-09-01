#### 4. Median of Two Sorted Arrays
Given two sorted arrays nums1 and nums2 of size m and n respectively.
Return the median of the two sorted arrays.
<p align="center">
    <img src="https://github.com/asli18/leetcode/blob/master/004_example.png?raw=true" alt="004_example"/>
</p>
- 兩個排列好的 array, 只要找到兩個長度相加後中間的 index 就是中間值
    - 注意總長度是奇數 or 偶數, 回傳結果不同

```c
double findMedianSortedArrays(int* nums1, int nums1Size, int* nums2, int nums2Size)
{
    const bool odd = (nums1Size + nums2Size) & 1;
    const int med_idx = (nums1Size + nums2Size) >> 1;
    double sum[2] = {0};
    int data;


    for (int i = 0; i < (med_idx + 1); ++i) {
        if (nums1Size && nums2Size) {
            if (*nums1 < *nums2) {
                data = *nums1++;
                nums1Size -= 1;
            } else {
                data = *nums2++;
                nums2Size -= 1;
            }
        } else if (nums1Size) {
            data = *nums1++;
        } else {
            data = *nums2++;
        }

        sum[(i == med_idx)] = data;
    }

    return (odd) ? sum[1] : ((sum[0] + sum[1]) / 2);
}
```

