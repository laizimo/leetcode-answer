# Add Binary

**题目：**

Given two binary strings, return their sum (also a binary string).

**翻译：**

给定两个二进制字符串，返回它们的和(也是一个二进制字符串)。

**例子：**

a = `"11"`
b = `"1"`
Return `"100"`.

**思路：**

* 首先，我们判断两个字符串哪个长度比较大
* 然后定义一个函数，将长的字符串作为第一个参数输入，短的作为第二个参数输入
* 然后定义我们在定义的add函数中，将两个字符串反置，然后定义一个curry位，初始值为0
* 然后相加两个字符串的位数，然后去加上curry变量，判断相加值是否大于2，如果大于2，将值减去2，然后将curry设置为1；反之，则将它设置为0；
* 然后结束循环时，判断curry是否为1，如果为1，则放入数组中
* 然后将数组倒置合并

**代码实现：**

```javascript
/**
 * @param {string} a
 * @param {string} b
 * @return {string}
 */
var addBinary = function(a, b) {
    return a.length > b.length ? add(a, b) : add(b, a);
};

function add(a, b){
    let curry = 0;
    const arr = [];
    a = a.split('').reverse().join('');
    b = b.split('').reverse().join('');
    for(let i = 0; i < a.length; i++){
        let tmp = parseInt(a[i]) + curry;
        if(i < b.length){
            tmp += parseInt(b[i]);
        }
        if(tmp >= 2){
            tmp -= 2;
            curry = 1;
        }else{
            curry = 0;
        }
        arr.push(tmp);
    }
    if(curry) arr.push(curry);
    return arr.reverse().join('')
}
```

