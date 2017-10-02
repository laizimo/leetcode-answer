# Power of Three

**题目：**

Given an integer, write a function to determine if it is a power of three.

**翻译：**

给定一个整数，写一个函数去判断它是否是3的幂次方。

**思路：**

* 第一种：循环
* 设置一个初始值为1，然后进行循环
* 先判断该值与给定值的大小，如果相等，返回true；如果大于，返回false；
* 然后将该值乘以3

**代码实现：**

```javascript
/**
 * @param {number} n
 * @return {boolean}
 */
var isPowerOfThree = function(n) {
    let three = 1;
    while(true){
        if(three === n)
            return true;
        else if(three > n)
            return false;
        three *= 3;
    }
};
```

* 第二种：转换成字符串
* 首先，使用toString方法将它转化为3进制字符串
* 然后通过正则表达式判断

**代码实现：**

```javascript
/**
 * @param {number} n
 * @return {boolean}
 */
var isPowerOfThree = function(n) {
    let str = n.toString(3);
    return /^10*$/.test(str);
};
```