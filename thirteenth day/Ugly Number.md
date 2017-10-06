# Ugly Number

**题目：**

Write a program to check whether a given number is an ugly number.

Ugly numbers are positive numbers whose prime factors only include `2, 3, 5`. For example, `6, 8` are ugly while `14` is not ugly since it includes another prime factor `7`.

Note that `1` is typically treated as an ugly number.

**翻译：**

写一个程序去检测给定的数字是否是一个丑数。

丑数是一个正数，它们的因子中仅包含2，3，5.例如：6和8都是丑数，而14不是丑数，因为它包含了另一个因子7。

注意1是被作为丑数对待

**思路：**

* 首先，判断当前这个数是否为正数，如果不为正数，则返回false
* 构建循环，循环条件当num大于1
* 然后逐一去判断当前这个数是否会被2，3，5整除，如果可以，直接将num除以它们之中的一个。
* 如果不可以，返回false
* 最后，跳出循环，返回true

**代码实现：**

```javascript
/**
 * @param {number} num
 * @return {boolean}
 */
var isUgly = function(num) {
    if(num <= 0)
        return false;
    while(num > 1){
        if(num % 2 === 0)
            num /= 2;
        else if(num % 3 === 0)
            num /= 3;
        else if(num % 5 === 0)
            num /= 5;
        else
            return false;
    }
    return true;
};
```

