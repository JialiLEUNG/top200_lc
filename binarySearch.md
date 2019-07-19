<!-- GFM-TOC -->
* [1. 求开方](#1-求开方)
* [2. 大于给定元素的最小元素](#2-大于给定元素的最小元素)
* [3. 有序数组的 Single Element](#3-有序数组的-single-element)
* [4. 第一个错误的版本](#4-第一个错误的版本)
* [5. 旋转数组的最小数字](#5-旋转数组的最小数字)
* [6. 查找区间](#6-查找区间)
<!-- GFM-TOC -->


# 1. 求开方
```python
#python

class Solution(object):
    def mySqrt(self, x):
        """
        :type x: int
        :rtype: int
        """
        if x <= 1:
            return x
        
        left = 0
        right = x
        
        while left <= right:
            mid = left + (right - left)/2
            sqrt = x / mid
            if sqrt == mid:
                return mid
            if sqrt < mid:
                right = mid - 1
            elif sqrt > mid:
                left = mid + 1
        return right
```
