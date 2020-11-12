#### [主要元素](https://leetcode-cn.com/problems/find-majority-element-lcci/)

> 数组中占比超过一半的元素称之为主要元素。给定一个**整数**数组，找到它的主要元素。若没有，返回-1。

示例 1：

```
输入：[1,2,5,9,5,9,5,5,5]
输出：5
```

示例 2：

```
输入：[3,2]
输出：-1
```

示例 3：

```
输入：[2,2,1,1,1,2,2]
输出：2
```

> 来源：力扣（LeetCode）
> 链接：https://leetcode-cn.com/problems/find-majority-element-lcci
> 著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。



```python
def majorityElement(nums: List[int]) -> int:
    if nums is None or len(nums) == 0:
        return None
    dic = {}

    for i in range(0, len(nums)):
        if dic.get(nums[i]) is None:
            dic.update({nums[i]: 1})
        else:
            dic.update({nums[i]: dic.get(nums[i]) + 1})
        if dic.get(nums[i]) > len(nums) >> 2:
            return nums[i]
    return -1
```

```python
def majorityElement(nums: List[int]) -> int:
    if nums is None or len(nums) == 0:
        return None
    dic = {}
    for i in range(0, len(nums)):
        if dic.get(nums[i]) is None:
            dic.update({nums[i]: 1})
        else:
            dic.update({nums[i]: dic.get(nums[i]) + 1})
    while dic:
        temp = dic.popitem()
        if temp[1] > len(nums) / 2:
            return temp[0]
    return -1
```



