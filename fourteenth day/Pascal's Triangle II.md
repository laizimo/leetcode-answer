# Pascal's Triangle II

**题目：**

Given an index *k*, return the *k*th row of the Pascal's triangle.

**翻译：**

给定一个索引k，返回Pascal三角形的第k行

**例子：**

For example, given *k* = 3,
Return `[1,3,3,1]`.

**思路：**

* 首先，生成一个Pascal三角形
* 每行的数组都是之前一行的数组两个元素的和，然后在首尾插入1的结果
* 然后返回pascal对应的下标

**代码实现：**

```javascript
/**
 * @param {number} rowIndex
 * @return {number[]}
 */
var getRow = function(rowIndex) {
    const pascal = [[1]];
    for(let i = 1; i <= rowIndex; i++){
        let prev = pascal[i - 1];
        let arr = [];
        arr.push(prev[0]);
        for(let i = 0; i < prev.length - 1; i++){
            arr.push(prev[i] + prev[i + 1]);
        }
        arr.push(prev[prev.length - 1]);
        pascal.push(arr);
    }
    return pascal[rowIndex];
};
```

