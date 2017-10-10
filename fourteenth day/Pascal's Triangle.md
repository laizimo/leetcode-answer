# Pascal's Triangle

**题目：**

Given numRows, generate the first numRows of Pascal's triangle.

**翻译：**

给定numRows，生成第一个numRows的Pascal's triangle

**例子：**

For example, given numRows = 5,
Return
```
[
     [1],
    [1,1],
   [1,2,1],
  [1,3,3,1],
 [1,4,6,4,1]
]
```

**思路：**

* 首先，判断numRows是否等于0，如果等于零，将res设置成空数组，否则，将其设置成内含[1]的数组
* 之后，以numRows为基准，从1到numRows遍历
* 每次都保持，当前数组中的元素，是上一个数组中元素，放入第一项和最后一项，然后前一项与后一项相加
* 将计算出来的数组放入结果数组中
* 遍历完成之后，将结果数组返回

**代码实现：**

```javascript
/**
 * @param {number} numRows
 * @return {number[][]}
 */
var generate = function(numRows) {
    const res = numRows ? [[1]] : [];
    for(let i = 1; i < numRows; i++){
        let arr = res[i - 1];
        let curr = [];
        curr.push(arr[0]);
        for(let j = 0; j < arr.length - 1; j++){
            curr.push(arr[j] + arr[j+1]);
        }
        curr.push(arr[arr.length - 1]);
        res.push(curr);
    }
    return res;
};
```