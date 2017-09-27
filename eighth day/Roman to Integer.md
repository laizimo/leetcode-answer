# Roman to Integer

**题目：**

Given a roman numeral, convert it to an integer.

Input is guaranteed to be within the range from 1 to 3999.

**翻译：**

给定一个罗马数字，将他转换成一个整数

输入的数字的值满足在1到3999之间

**思路：**

> 分析：罗马数字一共有7个：I => 1, V => 5, X => 10, L => 50, C => 100, D => 500, M => 1000
>
> 当然罗马数字也遵循一个规则：左边的数字比右边的小时，需要去减掉它；当左边数字比右边数字大时，需要去加上它。

**代码实现：**

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var romanToInt = function(s) {
    const obj = {'I': 1, 'V': 5, 'X': 10, 'L': 50, 'C': 100, 'D': 500, 'M': 1000};
    let sum = 0;
    for(let i = 0; i < s.length; i++){
        if(i == s.length - 1){
            sum += obj[s[i]];
        }else if(obj[s[i]] >= obj[s[i+1]]){
            sum += obj[s[i]];
        }else{
            sum -= obj[s[i]];
        }
    }
    return sum;
};
```