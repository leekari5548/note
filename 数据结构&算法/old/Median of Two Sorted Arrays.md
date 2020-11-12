### [Median of Two Sorted Arrays](https://leetcode-cn.com/problems/median-of-two-sorted-arrays/)



> Given two sorted arrays nums1 and nums2 of size m and n respectively, return the median of the two sorted arrays.
>
> Follow up: The overall run time complexity should be O(log (m+n)).

**Example 1:**

```
Input: nums1 = [1,3], nums2 = [2]
Output: 2.00000
Explanation: merged array = [1,2,3] and median is 2.
```

**Example 2:**

```
Input: nums1 = [1,2], nums2 = [3,4]
Output: 2.50000
Explanation: merged array = [1,2,3,4] and median is (2 + 3) / 2 = 2.5.
```

**Example 3:**

```
Input: nums1 = [0,0], nums2 = [0,0]
Output: 0.00000
```

**Example 4:**

```
Input: nums1 = [], nums2 = [1]
Output: 1.00000
```

**Example 5:**

```
Input: nums1 = [2], nums2 = []
Output: 2.00000
```

> Constraints:
>
> nums1.length == m
> nums2.length == n
> 0 <= m <= 1000
> 0 <= n <= 1000
> 1 <= m + n <= 2000
> -106 <= nums1[i], nums2[i] <= 106

>来源：力扣（LeetCode）
>链接：https://leetcode-cn.com/problems/median-of-two-sorted-arrays
>著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。



```python
def findMedianSortedArrays(nums1: List[int], nums2: List[int]) -> float:
    totalList = [0] * (len(nums1) + len(nums2))
    i = idx1 = idx2 = 0
    while idx1 != len(nums1) and idx2 != len(nums2):
        if nums1[idx1] > nums2[idx2]:
            totalList[i] = nums2[idx2]
            idx2 += 1
        else:
            totalList[i] = nums1[idx1]
            idx1 += 1
        i += 1
    if len(nums1) > idx1:
        while len(nums1) != idx1:
            totalList[i] = nums1[idx1]
            idx1 += 1
            i += 1
    if len(nums2) > idx2:
        while len(nums2) != idx2:
            totalList[i] = nums2[idx2]
            idx2 += 1
            i += 1
    mid = len(totalList) // 2
    if len(totalList) % 2:
        return float(totalList[mid])
    else:
        return float((totalList[mid] + totalList[mid - 1]) / 2)
      
      
if __name__ == '__main__':
    list1 = [1, 2]
    list2 = [3, 4]
    print(findMedianSortedArrays(list1, list2))
```



