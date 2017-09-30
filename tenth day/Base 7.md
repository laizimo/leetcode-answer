# Base 7

**题目：**

Given an integer, return its base 7 string representation.

**翻译：**

给定一个整数，返回它的基于7的代表字符串

**例子：**

```
Input: 100
Output: "202"
```

```
Input: -7
Output: "-10"
```

**思路：**

* 使用toString函数

**代码实现：**

```javascript
/**
 * @param {number} num
 * @return {string}
 */
var convertToBase7 = function(num) {
    return num.toString(7);
};
```