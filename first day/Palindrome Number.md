# Palindrome Number

**题目：**

Determine whether an integer is a palindrome. Do this without extra space.

**翻译：**

判断一个整数是否是一个回文。没有额外的空间。

**思路：**

* 将其转化成字符串，然后将其分割之后，转换数组，然后将数组拼接
* 最后比较两个字符串是否相等

```javascript
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function(x) {
    const str = '' + x;
    const reverseStr = str.split('').reverse().join('');
    return str === reverseStr;
};
```

