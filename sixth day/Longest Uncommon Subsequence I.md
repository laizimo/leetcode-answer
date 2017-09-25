# Longest Uncommon Subsequence I

**题目：**

Given a group of two strings, you need to find the longest uncommon subsequence of this group of two strings. The longest uncommon subsequence is defined as the longest subsequence of one of these strings and this subsequence should not be **any**subsequence of the other strings.

A **subsequence** is a sequence that can be derived from one sequence by deleting some characters without changing the order of the remaining elements. Trivially, any string is a subsequence of itself and an empty string is a subsequence of any string.

The input will be two strings, and the output needs to be the length of the longest uncommon subsequence. If the longest uncommon subsequence doesn't exist, return -1.

**翻译：**

给定两个字符串，你需要去找到在两个字符串中的最长不同子序列。最长的不寻常的子序列被定义为这些字符串之一的最长子序列，而这个子序列不应该是其他字符串的任何序列。

子序列是可以通过删除一些字符而不改变剩余元素的顺序从一个序列导出的序列。 简而言之，任何字符串本身都是一个子序列，空字符串是任何字符串的子序列。

输入将是两个字符串，输出需要是最长的不常见子序列的长度。 如果最长不常见的子序列不存在，则返回-1。

**例子：**

```
Input: "aba", "cdc"
Output: 3
Explanation: The longest uncommon subsequence is "aba" (or "cdc"), 
because "aba" is a subsequence of "aba", 
but not a subsequence of any other strings in the group of two strings. 
```

**思路：**

* 最长的子序列就是字符串本身，所以如果两个字符串不相等的时候，只需要返回两个字符串中最长字符串的长度就可以了。如果两个字符串相等，则返回-1.

**代码实现：**

```javascript
/**
 * @param {string} a
 * @param {string} b
 * @return {number}
 */
var findLUSlength = function(a, b) {
    if(a !== b){
        if(a.length > b.length)
            return a.length;
        else
            return b.length;
    }else
        return -1;
};
```

