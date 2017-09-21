# Fizz Buzz

**题目：**



Write a program that outputs the string representation of numbers from 1 to *n*.

But for multiples of three it should output “Fizz” instead of the number and for the multiples of five output “Buzz”. For numbers which are multiples of both three and five output “FizzBuzz”.



**翻译：**



写一个程序去输出从1到n的数字的字符串。



但是当这个数是3的倍数时，输出“Fizz”代替数字，当该数是5的倍数时输出“Buzz”代替，当数字即是3的倍数又是5的倍数时，输出“FizzBuzz”代替



**例子：**



```
n = 15,

Return:
[
    "1",
    "2",
    "Fizz",
    "4",
    "Buzz",
    "Fizz",
    "7",
    "8",
    "Fizz",
    "Buzz",
    "11",
    "Fizz",
    "13",
    "14",
    "FizzBuzz"
]
```



**思路：**



* 首先，先去判断它是否是15的陪数。如果是，则使用“FizzBuzz”代替
* 之后，判断它是否为3的倍数。如果是，则使用“Fizz”代替
* 然后，判断它是否为5的倍数。如果是，则使用“Buzz”代替
* 最后，如果都不是，则使用原数字



**代码实现：**



```javascript
/**
 * @param {number} n
 * @return {string[]}
 */
var fizzBuzz = function(n) {
    var arr = [];
    for(var i = 1; i <= n; i++){
        if(i % 15 === 0){
            arr.push('FizzBuzz');
        }else if(i % 3 === 0){
            arr.push('Fizz');
        }else if(i % 5 === 0){
            arr.push('Buzz');
        }else{
            arr.push(i+ '');
        }
    }
    return arr;
};
```

