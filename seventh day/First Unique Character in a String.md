# First Unique Character in a String

**题目：**

Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1.

**翻译：**

给定一个字符串，找到其中第一个不重复的字符，并且返回它的下标。如果不存在，返回-1；

**例子：**

```
s = "leetcode"
return 0.

s = "loveleetcode",
return 2.
```

**思路：**

* 使用map进行每个字符的数量存贮
* 然后遍历字符串，返回map中当前字符为1的字符的下标

**代码实现：**

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var firstUniqChar = function(s) {
    const map = new Map();
    for(let i = 0; i < s.length; i++){
        if(!map.get(s[i]))
            map.set(s[i], 1);
        else{
            map.set(s[i], map.get(s[i]) + 1);
        }
    }
    for(let i = 0; i < s.length; i++){
        if(map.get(s[i]) === 1){
            return i;
        }
    }
    return -1;
};
```

