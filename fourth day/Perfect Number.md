# Perfect Number

**题目：**

We define the Perfect Number is a **positive** integer that is equal to the sum of all its **positive** divisors except itself. 

Now, given an **integer** n, write a function that returns true when it is a perfect number and false when it is not.

**翻译：**

我们定义一个完美数是一个它本身等于所有它的因子的和，除了它本身。

现在，给一个整数n，写一个函数去判断它是否是一个完美数字

**例子：**

```
Input: 28
Output: True
Explanation: 28 = 1 + 2 + 4 + 7 + 14
```

**思路：**

* 首先，如果是数字1的话，返回false
* 然后，设定一变量sum，初始值为1
* 从2开始循环，直到变量的平方大于num，然后将可以被num整除的变量相加起来
* 最后，返回sum和num的比较

**代码实现：**

```javascript
/**
 * @param {number} num
 * @return {boolean}
 */
var checkPerfectNumber = function(num) {
    if(num === 1) return false;
    let sum = 1;
    for(let i = 2; i * i <= num; i++){
        if(num % i === 0){
            sum += i;
            sum += num / i;
        }
    }
    return sum === num;
};
```

