1. [Leetcode ：167. Two Sum II - Input array is sorted (Easy)](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/).

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


2. [633. Sum of Square Numbers (easy)](https://leetcode.com/problems/sum-of-square-numbers/description/).
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


3. [345. Reverse Vowels of a String (Easy)](https://leetcode.com/problems/reverse-vowels-of-a-string/).

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



4. []
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


