# Power of Two

**题目：**

Given an integer, write a function to determine if it is a power of two.

**翻译：**

给定一个整数，写一个函数去判断它是否为2的幂次方数

**思路：**

* 将该数转化为2进制字符串
* 然后，使用正则表达式判断

**代码实现：**

```javascript
/**
 * @param {number} n
 * @return {boolean}
 */
var isPowerOfTwo = function(n) {
    const str = n.toString(2);
    return /^10*$/.test(str);
};
```