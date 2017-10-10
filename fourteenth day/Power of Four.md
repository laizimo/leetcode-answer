# Power of Four

**题目：**

Given an integer (signed 32 bits), write a function to check whether it is a power of 4.

**翻译：**

给予一个整数(32位的)，写一个函数去检测它是否为4的幂次方

**例子：**

Given num = 16, return true. Given num = 5, return false

**思路：**

* 将其转为以4为底的字符串
* 然后通过正则表达式判断它属否为10\*

**代码实现：**

```javascript
/**
 * @param {number} num
 * @return {boolean}
 */
var isPowerOfFour = function(num) {
    const str = num.toString(4);
    return /^10*$/.test(str);
};
```