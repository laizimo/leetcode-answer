# Longest Palindrome

**题目：**

Given a string which consists of lowercase or uppercase letters, find the length of the longest palindromes that can be built with those letters.

This is case sensitive, for example `"Aa"` is not considered a palindrome here.

**翻译：**

给定一个包含小写或大写字母的字符串，查找一个由这些字符构建的最长的一个回文字符串。

一种特殊情况，例如“Aa”在这里不被考虑成一个回文

**例子：**

```
Input:
"abccccdd"

Output:
7

Explanation:
One longest palindrome that can be built is "dccaccd", whose length is 7.
```

**思路：**

* 方法一：
* 将字符串拆分成一个数组，然后对数组进行排序
* 对数组进行遍历，如果数组的当前元素与后一个元素相等，则count加2，并且i变量也加2
* 如果不相等，则i变量加1
* 最后，去判断count的值与s字符串的长度之间是否相等，相等就表示所以字符都被使用了
* 不相等的话，则需要加1，因为需要一个单字符

**代码实现：**

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var longestPalindrome = function(s) {
    if(s.length == 1) return 1;
    const arr = [...s];
    arr.sort();
    let count = 0;
    for(let i = 0; i < arr.length - 1;){
        if(arr[i] === arr[i+1]){
            count += 2;
            i += 2;
        }else{
            i++;
        }
    }
    if(count < arr.length){
        return count + 1;
    }
    return count;
};
```

- 方法二：时间复杂度O(n)
- 使用一个变量进行字符串每个字符数量的存储
- 首先，遍历字符串，对每个字符进行判断，如果对象中存在，则加1，不存在，则将该元素对应的值设置为1
- 然后遍历对象，对每一位的值，如果是偶数，则直接相加，如果是奇数，则加它减一位
- 最后，去判断count的值与s字符串的长度之间是否相等，相等就表示所以字符都被使用了
- 不相等的话，则需要加1，因为需要一个单字符

**代码实现：**

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var longestPalindrome = function(s) {
    let letters = {};
    let count = 0;
    for(let i = 0; i < s.length; i++){
        if(letters[s[i]]){
            letters[s[i]]++;
        }else{
            letters[s[i]] = 1;
        }
    }
    for(let i in letters){
        if(letters[i] % 2){
            count += letters[i] - 1;
        }else{
            count += letters[i];
        }
    }
    if(count !== s.length){
        return count + 1;
    }
    return count;
};
```

