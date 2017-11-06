# Find All Anagrams in a String

**题目：**

Given a string **s** and a **non-empty** string **p**, find all the start indices of **p**'s anagrams in **s**.

Strings consists of lowercase English letters only and the length of both strings **s** and **p** will not be larger than 20,100.

The order of output does not matter.

**翻译：**

给定一个字符串s和一个非空字符串p，找到s中所有p的字谜的开始下标。

字符串仅包含小写英文字母，并且所有字符串s和p的长度将不超过20100

不用在意输出的顺序

**例子：**

```
Input:
s: "cbaebabacd" p: "abc"

Output:
[0, 6]

Explanation:
The substring with start index = 0 is "cba", which is an anagram of "abc".
The substring with start index = 6 is "bac", which is an anagram of "abc".
```

```
Input:
s: "abab" p: "ab"

Output:
[0, 1, 2]

Explanation:
The substring with start index = 0 is "ab", which is an anagram of "ab".
The substring with start index = 1 is "ba", which is an anagram of "ab".
The substring with start index = 2 is "ab", which is an anagram of "ab".
```

**思路：**

* 首先，我们统计p中每个字母的数量
* 然后，我们统计s字符串开始的到p长度部分的字母的数量，然后进行一个差值统计
* 写一个judge函数来对象中字母是否都为0，若都为0，则返回true；否则，返回false
* 然后，写一个循环，来判断每次开头一个字母的数量去掉，然后加上p长度的后一位的字母，然后判断map对象

**代码实现：**

```javascript
/**
 * @param {string} s
 * @param {string} p
 * @return {number[]}
 */
var findAnagrams = function(s, p) {
    const index = [];
    const len = p.length;
    const map = {};
    for(let i = 0; i < len; i++){
        if(map[p[i]]) {
            map[p[i]]++;
        }else{
            map[p[i]] = 1;
        }
        if(map[s[i]]) {
            map[s[i]]--;
        } else {
            map[s[i]] = -1;
        }
    }
    if(judge(map))
        index.push(0);
    for(let i = 1; i <= s.length - len; i++){
        map[s[i - 1]]++;
        if(map[s[i + len - 1]]){
            map[s[i + len - 1]]--;
        }else{
            map[s[i + len - 1]] = -1;
        }
        if(judge(map))
            index.push(i);
    }
    return index;
};

function judge(obj){
    for(let key in obj){
        if(obj.hasOwnProperty(key)){
            if(obj[key] !== 0)
                return false;
        }
    }
    return true;
}
```

