# Convert a Number to Hexadecimal

**题目：**

Given an integer, write an algorithm to convert it to hexadecimal. For negative integer, two’s complement method is used.

**翻译：**

给定一个整数，写一个算法将它转换成16进制码。对于负数，需要使用二进制补码的方式

**例子：**

```
Input:
26

Output:
"1a"
```

```
Input:
-1

Output:
"ffffffff"
```

**思路：**

* 首先判断num是否为负数，如果是非负数，直接返回它的16进制码
* 如果是负数，首先取反，取反的方式可以是0xffffffff直接加上num的形式，然后再加一

**代码实现：**

```javascript
/**
 * @param {number} num
 * @return {string}
 */
var toHex = function(num) {
    if(num >= 0)
        return num.toString(16);
    else{
        return (0xffffffff + num + 1).toString(16);
    }
};
```