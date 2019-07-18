<!-- GFM-TOC -->
* [1. 有序数组的 Two Sum](#1-有序数组的-two-sum)
* [2. 两数平方和](#2-两数平方和)
* [3. 反转字符串中的元音字符](#3-反转字符串中的元音字符)
* [4. 回文字符串](#4-回文字符串)
* [5. 归并两个有序数组](#5-归并两个有序数组)
* [6. 最长子序列](#7-最长子序列)
* [7. 判断链表是否存在环](#6-判断链表是否存在环)
<!-- GFM-TOC -->

# 1. 有序数组的 Two Sum

[Leetcode ：167. Two Sum II - Input array is sorted (Easy)](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/).

Input: numbers={2, 7, 11, 15}, target=9

Output: index1=1, index2=2


```python
# python
def twoSum(self, numbers, target):
      """
      :type numbers: List[int]
      :type target: int
      :rtype: List[int]
      """
      i = 0
      j = len(numbers) - 1
        while i < j:
            sum = numbers[i] + numbers[j]
            if (sum == target):
                return [i+1,j+1]
            if (sum < target):
                i+=1
            else:j-=1
        return None
 ```       
        
```Java
// java
      int i = 0;
      int j = numbers.length;
      int sum;
      while (i < j){
            sum = numbers[i] + numbers[j]
            if (sum == target){
                  return new int[] {i, j}
            }
            if (sum < target){
                  i++
            } else { j++}
      }
      return null;
```


# 2. 两数平方和

[633. Sum of Square Numbers (easy)](https://leetcode.com/problems/sum-of-square-numbers/description/).
Given a non-negative integer c, your task is to decide whether there're two integers a and b such that a2 + b2 = c.

```python
# python
import math
    def judgeSquareSum(self, c):
        """
        :type c: int
        :rtype: bool
        """
        i = 0
        j = math.floor(math.sqrt(c))
        print(j)
        while i <= j:
            sums = i*i + j*j
            if sums == c:
                return True
            if sums > c:
                j-=1
            else: i+=1
        return False
```


```java
// java
```


# 3. 反转字符串中的元音字符 

[345. Reverse Vowels of a String (Easy)](https://leetcode.com/problems/reverse-vowels-of-a-string/).

```python
class Solution(object):
    def reverseVowels(self, s):
        """
        :type s: str
        :rtype: str
        """
        i = 0;
        j = len(s)-1
        vowel = ["a", "e", "i", "o", "u", "A", "E", "I", "O", "U"]
        res = list(s)
        
        while i < j:
            if s[i] not in vowel:
                i+=1
            elif s[j] not in vowel:
                j-=1
            else:
                temp = res[i]
                res[i] = res[j]
                res[j] = temp
                i+= 1
                j-=1
        return "".join(res)
```

```java

```



# 4. 回文字符串

[680. Valid Palindrome II (easy)](https://leetcode.com/problems/valid-palindrome-ii/description/).
```python
# python
class Solution(object):
    def validPalindrome(self, s):
        """
        :type s: str
        :rtype: bool
        """
        k = len(s)
        for i, j in zip(range(k/2), range(k-1, k/2, -1)):
            if s[i] != s[j]:
                return self.isPalin(s, i, j-1) or self.isPalin(s, i+1, j)
        return True
        
    
    def isPalin(self, s, i, j):
        while i < j:
            if s[i] != s[j]:
                return False
            i+=1
            j-=1
        return True
```

```java
// java
```

# 5. 归并两个有序数组

[88. Merge Sorted Array (Easy)](https://leetcode.com/problems/merge-sorted-array/description/).
```python
#python
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        """
        :type nums1: List[int]
        :type m: int
        :type nums2: List[int]
        :type n: int
        :rtype: None Do not return anything, modify nums1 in-place instead.
        """
        n1 = m - 1
        n2 = n - 1
        nTotal = m + n - 1
        while n1 >= 0 or n2 >= 0:
            if n1 < 0:
                nums1[nTotal] = nums2[n2]
                n2 -= 1
            elif n2 < 0:
                nums1[nTotal] = nums1[n1]
                n1 -= 1
            elif nums1[n1] > nums2[n2]:
                nums1[nTotal] = nums1[n1]
                n1-=1
            else:
                nums1[nTotal] = nums2[n2]
                n2-=1
            nTotal -= 1        
        
```


```java
# java

```

# 6. 最长子序列 

[524. Longest Word in Dictionary through Deleting (Medium)](https://leetcode.com/problems/longest-word-in-dictionary-through-deleting/description/)
```python
# python

```

```java

```

# 7. 判断链表是否存在环

[141. Linked List Cycle (Easy)](https://leetcode.com/problems/linked-list-cycle/description/).
```python
# python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def hasCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        if head == None:
            return False
        
        slow = head
        fast = head.next
        
        while slow != None and fast != None and fast.next != None:
            if slow == fast:
                return True
            slow = slow.next
            fast = fast.next.next
        return False

```

```java
# java
```









