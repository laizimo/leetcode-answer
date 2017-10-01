# Happy Number

**题目：**

Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.

**翻译：**

写一个算法去判断一个数字是否是'happy'的

一个happy数是可以通过以下过程来定义：开始于任何一个正整数，代替这个数字通过每一位的平方和，并且不断重复这个过程直到数字等于1，或者它在一个圆中无线循环，其中不包括1。那些过程最终为1的是happy数

**例子：**

```
19 is a happy number

12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```

**思路：**

* 首先，写一个计算当前数字每一位平方和的函数
* 然后，使用一个数组将当前元素存储起来，然后调用函数的平方和，去进行判断结果是否为1，如果为1，返回true；
* 再判断它是否存在于之前的数组中，如果存在，则返回false；如果不存在，则将当前元素放入数组，然后i加一

**代码实现：**

```javascript
/**
 * @param {number} n
 * @return {boolean}
 */
var isHappy = function(n) {
    if(n === 1)
        return true;
    const arr = [n];
    let i = 0;
    while(true){
        let sum = calculSum(arr[i]);
        if(sum === 1)
            return true;
        if(arr.indexOf(sum) === -1){
            arr.push(sum);
            i++;
        }else{
            return false;
        }
    }
};

function calculSum(n){
    let sum = 0;
    while(true){
        if(n < 10){
            sum += n**2;
            break;
        }
        let dig = n % 10;
        sum += dig ** 2;
        n = Math.floor(n / 10);
    }
    return sum;
}
```