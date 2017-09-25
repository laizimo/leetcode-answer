# Ransom Note

**题目：**

Given an arbitrary ransom note string and another string containing letters from all the magazines, write a function that will return true if the ransom note can be constructed from the magazines ; otherwise, it will return false.

Each letter in the magazine string can only be used once in your ransom note.

**翻译：**

给定一个任意的赎金票据字符串和另一个包含所有杂志的字母的字符串，写一个函数，如果可以从杂志中构建赎金票据，则返回true; 否则会返回false。

杂志字符串中的每个字母只能在您的赎金笔记中使用一次。

**例子：**

```
canConstruct("a", "b") -> false
canConstruct("aa", "ab") -> false
canConstruct("aa", "aab") -> true
```

**思路：**

* 首先将两个字符串拆分成两个数组
* 然后遍历，前面的note string，如果在两个数组中都能找到对应的元素，那么移除元素
* 如果在magazine中找不到对应的元素，就返回false
* 否则，结束循环之后，返回true

**代码实现：**

```javascript
/**
 * @param {string} ransomNote
 * @param {string} magazine
 * @return {boolean}
 */
var canConstruct = function(ransomNote, magazine) {
    const str1 = Array.from(ransomNote);
    const str2 = Array.from(magazine);
    while(str1.length){
        let i = 0;
        let index = str2.indexOf(str1[i]);
        if(index === -1){
            return false;
        }else{
            str1.shift();
            str2.splice(index, 1);
        }
    }
    return true;
};
```