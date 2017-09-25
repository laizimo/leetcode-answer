# Excel Sheet Column Number

**题目：**

Related to question Excel Sheet Column Title

Given a column title as appear in an Excel sheet, return its corresponding column number.

**翻译：**

相关的问题[Excek表列标题]

给你一个在一个Excel表中出现的列标题，返回它相应的列数

**例子：**

```
    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
```

**思路：**

* 这和一个二进制数到整数类似，只是以26为基数

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var titleToNumber = function(s) {
    let col = 0;
    const len = s.length;
    const char = 'A'.charCodeAt();
    for(let i = 0; i < len; i++){
        col += (s[i].charCodeAt() - char + 1)*( 26 ** (len - 1 - i));
    }
    return col;
};
```