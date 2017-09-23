# Add Digits

**题目：**



Given a non-negative integer `num`, repeatedly add all its digits until the result has only one digit. 

For example:

Given `num = 38`, the process is like: `3 + 8 = 11`, `1 + 1 = 2`. Since `2` has only one digit, return it.

**Follow up:**
Could you do it without any loop/recursion in O(1) runtime?



**翻译：**



给一个非负整数num，重复增加它的所有位数之后直到结果只剩下一位

例如：

给一个num为38，过程是：3+8=11，1+1=2。因为2只有1位，返回它。

> 要求：你可以在不使用循环或者递归的情况下，即时间复杂度是O(1)



**思路：**



* 你可以在脑子中想象一下，从1-9之后，10-18，19-27都是一个循环
* 所以，所有的数都可以在被9取余后算出
* 除了0，和整除的情况下，其他的数都是正确的。当输入0时，需要返回0；当取余为0时，需要返回9



```javascript
/**
 * @param {number} num
 * @return {number}
 */
var addDigits = function(num) {
    if(!num)
        return 0;
    else{
        return num % 9 ? num % 9 : 9;
    }
};
```





