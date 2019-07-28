<!-- GFM-TOC -->
* [1. 数组中两个数的和为给定值](#1-数组中两个数的和为给定值)
* [2. 判断数组是否含有重复元素](#2-判断数组是否含有重复元素)
* [3. 最长和谐序列](#3-最长和谐序列)
* [4. 最长连续序列](#4-最长连续序列)
<!-- GFM-TOC -->

## The following summary is from GeeksforGeeks at https://www.geeksforgeeks.org/difference-between-hashmap-and-hashset/
**HashSet** is implementation of **Set** Interface which does not allow duplicate value. The main thing is, objects that are stored in HashSet must override equals() for check for equality and hashCode() methods for no duplicate value are stored in our set.

**HashMap** is an implementation of **Map** Interface, which map a key to value. Duplicate keys are not allowed in a map.Basically Map Interface has two implementation classes HashMap and TreeMap. The main difference is TreeMap maintains order of the objects but HashMap will not. HashMap allows null values and null keys.

Both HashSet and HashMap are not synchronized.


# 1. 数组中两个数的和为给定值

[1. Two Sum (Easy)](https://leetcode.com/problems/two-sum/description/)


```java
    public int[] twoSum(int[] nums, int target) {
        HashMap<Integer, Integer> indexForNumber = new HashMap<>();
        for (int i = 0; i < nums.length; i++){
            if (indexForNumber.containsKey(target - nums[i])){
                return new int[]{indexForNumber.get(target - nums[i]), i};
            }
            else indexForNumber.put(nums[i],i);
        }
        return null;
    }
}
```

# 2. 判断数组是否含有重复元素

[217. Contains Duplicate (Easy)](https://leetcode.com/problems/contains-duplicate/description/)

```java
# java
public boolean containsDuplicate(int[] nums) {
        HashSet<Integer> res = new HashSet<>();
        for(int num:nums){
            res.add(num);
        }
        return res.size() < nums.length;
    }
```

# 3. 最长和谐序列

[594. Longest Harmonious Subsequence (Easy)](https://leetcode.com/problems/longest-harmonious-subsequence/description/)

```html
Input: [1,3,2,2,5,2,3,7]
Output: 5
Explanation: The longest harmonious subsequence is [3,2,2,2,3].
```

和谐序列中最大数和最小数之差正好为 1，应该注意的是序列的元素不一定是数组的连续元素。

```java
public int findLHS(int[] nums) {
    Map<Integer, Integer> countForNum = new HashMap<>();
    for (int num : nums) {
        countForNum.put(num, countForNum.getOrDefault(num, 0) + 1);
    }
    int longest = 0;
    for (int num : countForNum.keySet()) {
        if (countForNum.containsKey(num + 1)) {
            longest = Math.max(longest, countForNum.get(num + 1) + countForNum.get(num));
        }
    }
    return longest;
}
```

# 4. 最长连续序列

[128. Longest Consecutive Sequence (Hard)](https://leetcode.com/problems/longest-consecutive-sequence/description/)

```html
Given [100, 4, 200, 1, 3, 2],
The longest consecutive elements sequence is [1, 2, 3, 4]. Return its length: 4.
```

要求以 O(N) 的时间复杂度求解。

```java
public int longestConsecutive(int[] nums) {
    Map<Integer, Integer> countForNum = new HashMap<>();
    for (int num : nums) {
        countForNum.put(num, 1);
    }
    for (int num : nums) {
        forward(countForNum, num);
    }
    return maxCount(countForNum);
}

private int forward(Map<Integer, Integer> countForNum, int num) {
    if (!countForNum.containsKey(num)) {
        return 0;
    }
    int cnt = countForNum.get(num);
    if (cnt > 1) {
        return cnt;
    }
    cnt = forward(countForNum, num + 1) + 1;
    countForNum.put(num, cnt);
    return cnt;
}

private int maxCount(Map<Integer, Integer> countForNum) {
    int max = 0;
    for (int num : countForNum.keySet()) {
        max = Math.max(max, countForNum.get(num));
    }
    return max;
}
```



<br><div align="center"><img width="320px" src="https://cs-notes-1256109796.cos.ap-guangzhou.myqcloud.com/other/公众号海报6.png"></img></div>
