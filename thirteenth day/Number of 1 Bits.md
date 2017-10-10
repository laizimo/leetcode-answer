# Number of 1 Bits

**题目：**

Write a function that takes an unsigned integer and returns the number of ’1' bits it has (also known as the [Hamming weight](https://en.wikipedia.org/wiki/Hamming_weight)).

**翻译：**

写一个函数去计算一个正数，并且返回二进制中含有的1的数量(也众所周知的海明重量)

**例子：**

For example, the 32-bit integer ’11' has binary representation `00000000000000000000000000001011`, so the function should return 3.

**思路：**

* 首先，将它转成二进制字符串
* 然后，计算字符串中的1字符的数量

**代码实现：**

```javascript
/**
 * @param {number} n - a positive integer
 * @return {number}
 */
var hammingWeight = function(n) {
    let str = n.toString(2);
    let count = 0;
    for(let i = 0; i < str.length; i++){
        if(str[i] === '1')
            count++;
    }
    return count;
};
```

