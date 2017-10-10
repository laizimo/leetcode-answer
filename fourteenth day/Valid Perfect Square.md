# Valid Perfect Square

**题目：**

Given a positive integer num, write a function which returns True if num is a perfect square else False.

**翻译：**

给定一个正数num，编写一个函数判断num是否为一个完美正方形，如果是返回true，否则返回false

**例子：**

```
Input: 16
Returns: True
```

```
Input: 14
Returns: False
```

**思路：**

* 设置一个变量，进行循环，如果它的乘积大于num，跳出循环
* 然后判断当前元素乘积是否为num

**代码实现：**

```javascript
/**
 * @param {number} num
 * @return {boolean}
 */
var isPerfectSquare = function(num) {
    let res = false;
    for(let i = 1; i * i <= num; i++){
        if(i * i === num)
            res = true;
    }
    return res;
};
```