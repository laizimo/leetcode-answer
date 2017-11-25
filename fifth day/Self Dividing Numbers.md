# Self Dividing Numbers

**题目：**

A self-dividing number is a number that is divisible by every digit it contains.

For example, ```128``` is a self-dividing number because ```128 % 1 == 0```, ```128 % 2 == 0```, and ```128 % 8 == 0```.

Also, a self-dividing number is not allowed to contain the digit zero.

Given a lower and upper number bound, output a list of every possible self dividing number, including the bounds if possible.

**翻译：**

一个自分数是一个被它包含的每一个数字分割的数。

例如，```128```是一个自分数因为```128 % 1 == 0```，```128 % 2 == 0```, 和```128 % 8 == 0```。

同时，一个自分数不被允许包含数字0。

给定一个较小和较大的整数范围，输出一个可能为自分数的列表，包含边界。

**例子：**

```javascript
Input: 
left = 1, right = 22
Output: [1, 2, 3, 4, 5, 6, 7, 8, 9, 11, 12, 15, 22]
```

**思路：**

* 分割一个整数的每一位，然后对它们进行整除判断，如果满足条件，将其放入结果列表中；反之，则跳过。

**代码实现：**

```javascript
/**
 * @param {number} left
 * @param {number} right
 * @return {number[]}
 */
var selfDividingNumbers = function(left, right) {
    const arr = [];
    for(let i = left; i <= right; i++){
        if(judge(i)){
            arr.push(i);
        }
    }
    return arr;
};

function judge(num){
    const arr = [];
    const native = num;
    while(num){
        let item = num % 10;
        arr.push(item);
        num = (num - item) / 10;
    }
    for(let i = 0; i < arr.length; i++){
        let tmp = arr[i];
        if(native % tmp !== 0) return false;
    }
    return true;
}
```