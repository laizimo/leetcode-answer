# Number of Segments in a String

**题目：**

Count the number of segments in a string, where a segment is defined to be a contiguous sequence of non-space characters.

Please note that the string does not contain any **non-printable** characters.

**翻译：**

统计一个字符串中片段的数量，片段被定义为没有空白字符的连续字串。

请注意字符串中不含有非空白字符

**例子：**

```
Input: "Hello, my name is John"
Output: 5
```

**思路：**

* 首先，使用正则表达式将两边的空白字符
* 然后，将中间的多个空白字符替换成一个空白字符
* 然后使用split分割它们，计算出整个数组的长度

**代码实现：**

```javascript
/**
 * @param {string} s
 * @return {number}
 */
var countSegments = function(s) {
    let str1 = s.replace(/^\s+|\s+$/g, '');
    str1 = str1.replace(/\s+/g, ' ');
    if(!str1)
        return 0;
    return str1.split(' ').length;
};
```

