<!-- GFM-TOC -->
* [1. 字符串循环移位包含](#1-字符串循环移位包含)
* [2. 字符串循环移位](#2-字符串循环移位)
* [3. 字符串中单词的翻转](#3-字符串中单词的翻转)
* [4. Valid Anagram](#4Valid Anagram)
* [5. 计算一组字符集合可以组成的回文字符串的最大长度](#5-计算一组字符集合可以组成的回文字符串的最大长度)
* [6. 字符串同构](#6-字符串同构)
* [7. 回文子字符串个数](#7-回文子字符串个数)
* [8. 判断一个整数是否是回文数](#8-判断一个整数是否是回文数)
* [9. 统计二进制字符串中连续 1 和连续 0 数量相同的子字符串个数](#9-统计二进制字符串中连续-1-和连续-0-数量相同的子字符串个数)
<!-- GFM-TOC -->


# 1. 字符串循环移位包含

[编程之美 3.1](#)

```html
s1 = AABCD, s2 = CDAA
Return : true
```

给定两个字符串 s1 和 s2，要求判定 s2 是否能够被 s1 做循环移位得到的字符串包含。

s1 进行循环移位的结果是 s1s1 的子字符串，因此只要判断 s2 是否是 s1s1 的子字符串即可。

Similar topic at [189. Rotate Array(Easy)](https://leetcode.com/problems/rotate-array/).

```java
# java
public void rotate(int[] nums, int k) {
        int n = nums.length;
        int[] dup = new int[n];
        for (int i = 0; i< n; i++){
            dup[(i+k)%n] = nums[i];
        }
        for (int i = 0; i < n; i++){
            nums[i] = dup[i];
        }
    }

```

# 2. 字符串循环移位

[编程之美 2.17](#)

```html
s = "abcd123" k = 3
Return "123abcd"
```

将字符串向右循环移动 k 位。

将 abcd123 中的 abcd 和 123 单独翻转，得到 dcba321，然后对整个字符串进行翻转，得到 123abcd。



# 3. 字符串中单词的翻转

[程序员代码面试指南](#)

```html
s = "I am a student"
Return "student a am I"
```

将每个单词翻转，然后将整个字符串翻转。

# 4. Valid Anagram

[242. Valid Anagram (Easy)](https://leetcode.com/problems/valid-anagram/description/)

```html
s = "anagram", t = "nagaram", return true.
s = "rat", t = "car", return false.
```

可以用 HashMap 来映射字符与出现次数，然后比较两个字符串出现的字符数量是否相同。

由于本题的字符串只包含 26 个小写字符，因此可以使用长度为 26 的整型数组对字符串出现的字符进行统计，不再使用 HashMap, 但是我用了hashmap。

```java
# java
public boolean isAnagram(String s, String t) {
        Map<Character, Integer> dict = new HashMap<>();
        for (char i:s.toCharArray()){
            dict.put(i, dict.getOrDefault(i, 0)+1);
        }
        for (char i:t.toCharArray()){
            dict.put(i, dict.getOrDefault(i, 0) - 1);
        }
        
        for (char i:dict.keySet()){
            if (dict.get(i) != 0){
                return false;
            }
        }
        return true;    
    }
```

# 5. 计算一组字符集合可以组成的回文字符串的最大长度

[409. Longest Palindrome (Easy)](https://leetcode.com/problems/longest-palindrome/description/)

```html
Input : "abccccdd"
Output : 7
Explanation : One longest palindrome that can be built is "dccaccd", whose length is 7.
```

使用长度为 256 的整型数组来统计每个字符出现的个数，每个字符有偶数个可以用来构成回文字符串。

因为回文字符串最中间的那个字符可以单独出现，所以如果有单独的字符就把它放到最中间。

```java
public int longestPalindrome(String s) {
        int[] count = new int[128]; // or change 128 to 256 for extended ascii table.
        for (char i:s.toCharArray()){
            count[i]++;
        }
        int palindrome = 0;
        for (int i:count){
            palindrome += i/2 * 2;
        }
        if (palindrome < s.length()){
            palindrome+=1;
        }
        return palindrome;
    }
```

# 6. 字符串同构

[205. Isomorphic Strings (Easy)](https://leetcode.com/problems/isomorphic-strings/description/)

```html
Given "egg", "add", return true.
Given "foo", "bar", return false.
Given "paper", "title", return true.
```

记录一个字符上次出现的位置，如果两个字符串中的字符上次出现的位置一样，那么就属于同构。

```java
# java
public boolean isIsomorphic(String s, String t) {
        int[] countS = new int[128];
        int[] countT = new int[128];
        
        for (int i=0; i < s.length(); i++){
            char charS = s.charAt(i);
            char charT = t.charAt(i);
            if (countS[charS] != countT[charT]){
                return false;
            }
            countS[charS] = i + 1;
            countT[charT] = i + 1;
        }
        return true; 
    }
```

# 7. 回文子字符串个数

[647. Palindromic Substrings (Medium)](https://leetcode.com/problems/palindromic-substrings/description/)

```java
# java
private int count = 0;
    public int countSubstrings(String s) {
        for (int i = 0; i < s.length(); i++){
            extendPalindrome(s, i, i);
            extendPalindrome(s, i, i + 1);
        }
        return count;
    }
    private void extendPalindrome(String s, int left, int right){
        while (left >=0 && right < s.length() && s.charAt(left) == s.charAt(right)){
            left--;
            right++;
            count++;
        }
    }
```

# 8. 判断一个整数是否是回文数

[9. Palindrome Number (Easy)](https://leetcode.com/problems/palindrome-number/description/)

要求不能使用额外空间，也就不能将整数转换为字符串进行判断。

将整数分成左右两部分，右边那部分需要转置，然后判断这两部分是否相等。

```java
# not solved
```

# 9. 统计二进制字符串中连续 1 和连续 0 数量相同的子字符串个数

[696. Count Binary Substrings (Easy)](https://leetcode.com/problems/count-binary-substrings/description/)

```html
Input: "00110011"
Output: 6
Explanation: There are 6 substrings that have equal number of consecutive 1's and 0's: "0011", "01", "1100", "10", "0011", and "01".
```

```java
# not solved
```

