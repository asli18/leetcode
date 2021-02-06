#### 88. Merge Sorted Array
Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.
- Note:
    The number of elements initialized in nums1 and nums2 are m and n respectively. You may assume that **nums1 has enough space (size that is equal to m + n)** to hold  additional elements from nums2.
    - m: nums1 內的data有效長度
    - n: nums2 內的data有效長度
    - `nums1Size = m + n`
<p align="center">
    <img src="https://github.com/asli18/leetcode/blob/master/088_example.png?raw=true" alt="088_example"/>
</p>

- 從 nums1 的最後面多的空間開始擺最大值，就不用顧慮會蓋掉原本值
<div style="page-break-after: always;"></div>

```c
void merge(int* nums1, int nums1Size, int m,
           int* nums2, int nums2Size, int n)
{
    if (nums1Size == m)
        return;
    
    int *data = nums1 + nums1Size - 1;
    int *n1_end;
    int *n2_end;
    
    if (m)
        n1_end = nums1 + m - 1;
    if (n)
        n2_end = nums2 + n - 1;
    
    while (data >= nums1) {
        if ((n1_end >= nums1) && (n2_end >= nums2)) {
            if (*n1_end > *n2_end)
                *data = *n1_end--;
            else
                *data = *n2_end--;

        } else if (n1_end >= nums1) {
            *data = *n1_end--;
        } else {
            *data = *n2_end--;
        }
        *data--;
    }
}
```
