# Plus One

**题目：**

Given a non-negative integer represented as a non-empty array of digits, plus one to the integer.

You may assume the integer do not contain any leading zero, except the number 0 itself.

The digits are stored such that the most significant digit is at the head of the list.

**翻译：**

给定一个非负整数代表一个非空的数字数组，使得整数加一。

你可能强调整数并不包含任何前导0，除了数字0自身除外

数字被存储，使得最高有效数字位于列表的头部。

**思路：**

* 设置一个进位符，设置为0，然后使得数组的最后一位加一
* 之后遍历整个数组，然后每个当前元素，先加上进位符
* 然后进行判断，如果当前元素大于等于10的话，就将进位符置1，然后将当前元素减1
* 如果没有，则将进位符置为0
* 结束遍历之后，我们可以判断进位符是否为1，如果为1，就在数组开始处放入一个1
* 然后，返回结果数组

**代码实现：**

```javascript
/**
 * @param {number[]} digits
 * @return {number[]}
 */
var plusOne = function(digits) {
    let curry = 0;
    digits[digits.length - 1]++;
    for(let i = digits.length - 1; i >= 0; i--){
        digits[i] += curry;
        if(digits[i] >= 10){
            curry = 1;
            digits[i] -= 10;
        }else{
            curry = 0;
        }
    }
    if(curry)
        digits.unshift(curry);
    return digits;
};
```