# Reverse String

**题目：**



Write a function that takes a string as input and returns the string reversed.



**翻译：**



写一个函数可以将字符串作为输入，并且将反转的字符串作为输出



**例子：**



Given s = "hello", return "olleh".



**思路：**



将字符串的每个字符拆分成数组，然后将数组反转，之后将数组拼接成字符串返回



**代码实现：**



```javascript
/**
 * @param {string} s
 * @return {string}
 */
var reverseString = function(s) {
    return [...s].reverse().join('');
};
```

