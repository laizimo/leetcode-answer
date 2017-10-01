# Add Strings

**题目：**

Given two non-negative integers num1 and num2 represented as string, return the sum of num1 and num2

**翻译：**

给定两个使用字符串代表的非负整数num1和num2，返回num1和num2的和

**思路：**

* 这是一个大整数的计算，如果直接转化为整数进行计算会导致计算偏差
* 所以，使用按位加法，从倒数第一个元素开始计算，然后设置进位符carry
* 每次sum都会加上num1的当前元素和num2的当前元素和carry。
* 如果sum大于等于10，则将carry设置为1，然后sum减去10；如果小于10，则将carry设置为0
* 最后，判断carry是否为1，如果为1的话，则将元素放入数组中

**代码实现：**

```javascript
/**
 * @param {string} num1
 * @param {string} num2
 * @return {string}
 */
var addStrings = function(num1, num2) {
    if(num1.length > num2.length)
        return add(num1, num2);
    else
        return add(num2, num1);
};

function add(str1, str2){
    const len1 = str1.length;
    const len2 = str2.length;
    let carry = 0;
    const arr = [];
    for(let i = 1; i <= len1; i++){
        let sum = 0;
        if(i > len2)
            sum = parseInt(str1[len1 - i]) + carry;
        else
            sum = parseInt(str1[len1 - i]) + parseInt(str2[len2 - i]) + carry;
        if(sum >= 10){
            sum -= 10;
            carry = 1;
        }else
            carry = 0;
        arr.push(sum);
    }
    if(carry)
        arr.push(carry);
    return arr.reverse().join('');
}
```