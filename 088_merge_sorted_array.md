#### 88. Merge Sorted Array
Given two sorted integer arrays nums1 and nums2, merge nums2 into nums1 as one sorted array.

- Note:
    The number of elements initialized in nums1 and nums2 are m and n respectively.
    You may assume that **nums1 has enough space (size that is equal to m + n)** to hold  additional elements from nums2.
    - m: nums1 內的data有效長度
    - n: nums2 內的data有效長度
    - `nums1Size = m + n`
<p align="center">
    <img src="https://github.com/asli18/leetcode/blob/master/088_example.png?raw=true" alt="088_example"/>
</p>

- 從 nums1 的最後面多的空間開始擺最大值，就不用顧慮會蓋掉原本值

```c
void merge(int* nums1, int nums1Size, int m,
           int* nums2, int nums2Size, int n)
{
    int len = m + n;
    int *data = nums1 + nums1Size - 1;

    nums1 += m - 1;
    nums2 += n - 1;

    while (len--) {
        if (m && n) {
            if (*nums1 > *nums2) {
                *data = *nums1--;
                m--;
            } else {
                *data = *nums2--;
                n--;
            }
        } else if (m) {
            *data = *nums1--;
        } else {
            *data = *nums2--;
        }
        data -=1;
    }
}
```
