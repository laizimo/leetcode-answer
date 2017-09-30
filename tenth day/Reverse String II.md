# Reverse String II

**题目：**

Given a string and an integer k, you need to reverse the first k characters for every 2k characters counting from the start of the string. If there are less than k characters left, reverse all of them. If there are less than 2k but greater than or equal to k characters, then reverse the first k characters and left the other as original.

**翻译：**

给定一个字符串和一个整数k，从字符串的开头开始，对于每2k个字符，你需要去翻转第一部分的k个字符。如果剩余字符少于k，将他们所有的反转。如果少于2*k个，但是大于或等于k个字符，翻转第一部分的k个字符，剩余的不变

**例子：**

```
Input: s = "abcdefg", k = 2
Output: "bacdfeg"
```

**思路：**

* 首先，设置一个循环变量index
* 然后设置循坏，条件是index小于s的长度
* 然后截取s的index到index+k的部分
* 判断index除以k之后是偶数还是奇数，如果是奇数，则保持字符串不变；如果是偶数，则翻转字符串
* 最后，返回字符串

**代码实现：**

```javascript
/**
 * @param {string} s
 * @param {number} k
 * @return {string}
 */
var reverseStr = function(s, k) {
    let index = 0;
    let str = '';
    while(index < s.length){
        let sItem = s.slice(index, index + k);
        if(!((index / k) & 1)){
            str += sItem.split('').reverse().join('');
        }else{
            str += sItem;
        }
        index += k;
    }
    return str;
};
```