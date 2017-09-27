# Valid Anagram

**题目：**

Given two strings s and t, write a function to determine if t is an anagram of s.

For example,
s = "anagram", t = "nagaram", return true.
s = "rat", t = "car", return false.

**翻译：**

给定两个字符串s和t，写一个函数去判定t字符串是不是s的一个字谜

举例：
s = "anagram", t = "nagaram", 返回true
s = "rat", t = "car", 返回false

**思路：**

* 首先判断两个字符串长度是否相等，不相等直接返回false
* 然后将字符串的字符放入数组中，进行排序
* 之后遍历数组，判断两个数组是否相等，如果不相等，直接返回false
* 遍历完数组之后，表示字符都是相等的，返回true

**代码实现：**

```javascript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isAnagram = function(s, t) {
    if(s.length !== t.length){
        return false;
    }else{
        const len = s.length;
        const arr1 = [...s];
        const arr2 = [...t];
        arr1.sort();
        arr2.sort();
        for(let i = 0; i < len; i++){
            if(arr1[i] !== arr2[i])
                return false;
        }
        return true;
    }
};
```