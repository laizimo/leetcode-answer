# Repeated Substring Pattern

**题目：**

Given a non-empty string check if it can be constructed by taking a substring of it and appending multiple copies of the substring together. You may assume the given string consists of lowercase English letters only and its length will not exceed 10000.

**翻译：**

给定一个非空字符串，检测它是否可以被它的子串构成，并且多次添加这个子串的复制体。你可能强调给定的字符串仅由小写的英文字母组成，并且它的长度不超过10000.

**例子：**

```
Input: "abab"

Output: True

Explanation: It's the substring "ab" twice.
```

```
Input: "aba"

Output: False
```

```
Input: "abcabcabcabc"

Output: True

Explanation: It's the substring "abc" four times. (And the substring "abcabc" twice.)
```

**思路：**

* 编写一个函数，去检测执行长度的字串是否是重复的
* 然后从1开始增加，判断给定字符串是否由字串构成

**代码实现：**

```javascript
/**
 * @param {string} s
 * @return {boolean}
 */
var repeatedSubstringPattern = function(s) {
    const len = s.length;
    for(let i = 1; i * 2 <= len; i++){
        if(judgeString(s, i))
            return true;
    }
    return false;
};

function judgeString(s, dis){
    let tmp = s.substr(0, dis);
    let i = dis;
    while(i < s.length){
        let str = s.substr(i, dis);
        if(str !== tmp)
            return false;
        i += dis;
    }
    return true;
}
```