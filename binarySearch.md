<!-- GFM-TOC -->
* [1. 求开方](#1-求开方)
* [2. 大于给定元素的最小元素](#2-大于给定元素的最小元素)
* [3. 有序数组的 Single Element](#3-有序数组的-single-element)
* [4. 第一个错误的版本](#4-第一个错误的版本)
* [5. 旋转数组的最小数字](#5-旋转数组的最小数字)
* [6. 查找区间](#6-查找区间)
<!-- GFM-TOC -->


# 1. 求开方
[69. Sqrt(x) (Easy)](https://leetcode.com/problems/sqrtx/description/).
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


# 2. 大于给定元素的最小元素
[744. Find Smallest Letter Greater Than Target (Easy)](https://leetcode.com/problems/find-smallest-letter-greater-than-target/)

```python
class Solution:
    def nextGreatestLetter(self, letters, target):
        """
        :type letters: List[str]
        :type target: str
        :rtype: str
        """
        length = len(letters)
        left = 0
        right = length - 1
        
        while left <= right:
            mid = left + int((right - left) / 2)
            if letters[mid] <= target:
                left = mid + 1
            elif letters[mid] > target:
                right = mid - 1
        if left < length:
            return letters[left]
        else:
            return letters[0]
```

# 3. 有序数组的 Single Element
[540. Single Element in a Sorted Array (Medium)](https://leetcode.com/problems/single-element-in-a-sorted-array/description/).

```python
class Solution(object):
    def singleNonDuplicate(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        left = 0
        right = len(nums) - 1
        while left < right:
            mid = left + int(right - left) / 2
            if mid % 2 == 1:
                mid -= 1
            if nums[mid] == nums[mid + 1]:
                left = mid + 2
            else:
                right = mid
        return nums[left]
```


# 4. 第一个错误的版本
[278. First Bad Version (Easy)](https://leetcode.com/problems/first-bad-version/).
```python
# The isBadVersion API is already defined for you.
# @param version, an integer
# @return a bool
# def isBadVersion(version):

class Solution(object):
    def firstBadVersion(self, n):
        """
        :type n: int
        :rtype: int
        """
        left = 1
        right = n        
        while left < right:
            mid = left + (right-left)/2
            if isBadVersion(mid):
                right = mid
            else:
                left = mid + 1
        return left  
```
