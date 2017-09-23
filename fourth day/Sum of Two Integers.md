# Sum of Two Integers

**题目：**



Calculate the sum of two integers *a* and *b*, but you are **not allowed** to use the operator `+` and `-`.



**翻译：**



计算两个整数a和b的和，但是你不被允许去使用操作符+和-



**例子：**



Given *a* = 1 and *b* = 2, return 3.



**思路：**



> 由于没有看懂操作思路，只是翻译一下别人的思路，这种直接操作位的方式，有点难以理解



* 首先，看一下0+0=0，0+1=1，1+0=1, 1+1 = 0 是异或操作
* 然后可以知道1+1=2，可以看成 (1&1)<<1 = 2
* 那么结合第一步和第二步，不断的重复，知道(a&b)<<1为0



**代码实现：**



```javascript
/**
 * @param {number} a
 * @param {number} b
 * @return {number}
 */
var getSum = function(a, b) {
    if(b == 0) return a;
    
    const sum = a ^ b;
    const carry = (a & b) << 1;
    return getSum(sum, carry);
};
```

