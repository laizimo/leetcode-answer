# Isomorphic Strings

**题目：**

Given two strings **s** and **t**, determine if they are isomorphic.

Two strings are isomorphic if the characters in **s** can be replaced to get **t**.

All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character but a character may map to itself.

**翻译：**

给定两个字符串s和t，判断它们是否同构

如果s中的字符串可以被替换得到t，那么，两个字符串就是同构的。

保持字符串顺序的同时，所有a字符必须被另一个字符替换。不存在两个字符映射到相同字符，但是一个字符可能映射到它本身

**例子：**

Given `"egg"`, `"add"`, return true.

Given `"foo"`, `"bar"`, return false.

Given `"paper"`, `"title"`, return true.

**思路：**

* 首先，我们获取字符串的长度len
* 然后，我们将字符串t拆开成数组，然后将数组中相对应s字符串的部分进行替换
* 首先，我们命名一个映射表map，然后将未设置映射的字符，设置映射，同时保证不要重复设置映射
* 然后，对已设置映射的字符，进行替换
* 最后，比较t与arrT形成的字符串是否一致

**代码实现：**

```javascript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
var isIsomorphic = function(s, t) {
    const len = s.length, 
          map = new Map(),
          arrT = t.split('');
    const type = [];
    for(let i = 0; i < len; i++){
        if(map.has(s[i])){
            arrT[i] = map.get(s[i]);
        }else if(type.indexOf(t[i]) === -1){
            map.set(s[i], t[i]);
            type.push(t[i]);
        }else{
            arrT[i] = s[i];
        }
    }
    return t === arrT.join('');
};
```

