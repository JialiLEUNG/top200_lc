1. [Leetcode ：167. Two Sum II - Input array is sorted (Easy)](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/).

Input: numbers={2, 7, 11, 15}, target=9
Output: index1=1, index2=2


**python:**
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
        
        
**Java**
