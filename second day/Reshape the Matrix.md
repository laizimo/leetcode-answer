# Reshape the Matrix

**题目：**



In MATLAB, there is a very useful function called 'reshape', which can reshape a matrix into a new one with different size but keep its original data.

You're given a matrix represented by a two-dimensional array, and two **positive** integers **r** and **c** representing the **row** number and **column** number of the wanted reshaped matrix, respectively.

The reshaped matrix need to be filled with all the elements of the original matrix in the same **row-traversing** order as they were.

If the 'reshape' operation with given parameters is possible and legal, output the new reshaped matrix; Otherwise, output the original matrix.



**翻译：**



在MATLAB中，有一个非常有用的函数叫做重塑，即可以将一个矩阵重塑到一个新的具备不同尺寸但保持它的原数据的矩阵



你将被给予一个由二维数组代表的矩阵，和两个有效的整数r和c，分别代表着想要的重塑矩阵的行数和列数。



这个重塑举证需要用原矩阵的，且保持相同顺序的所有元素填充。



如果这个重塑操作被给予的参数是可能的和合法的，输出新的重塑矩阵；否则， 输出原来的矩阵。



**例子：**



```
Input: 
nums = 
[[1,2],
 [3,4]]
r = 1, c = 4
Output: 
[[1,2,3,4]]
Explanation:
The row-traversing of nums is [1,2,3,4]. The new reshaped matrix is a 1 * 4 matrix, fill it row by row by using the previous list.
```



> 例子解释：nums的行转变是[1, 2, 3, 4]。新重塑的矩阵是一个1*4的矩阵，使用原有列表一行一行地填充它



```
Input: 
nums = 
[[1,2],
 [3,4]]
r = 2, c = 4
Output: 
[[1,2],
 [3,4]]
Explanation:
There is no way to reshape a 2 * 2 matrix to a 2 * 4 matrix. So output the original matrix.
```



> 例子解释：这里没有办法去重塑一个2*2的矩阵到一个2\*4的矩阵，因此输出原矩阵



**思路：**



* 首先，我们需要去判断新矩阵的个数是否与原矩阵的个数相同。如果相同，则执行转换；反之，则返回原矩阵
* 经过第一步的判断，之后去建立一个r*c的二维数组
* 设置两个变量row=0和col=0
* 然后遍历原矩阵，每次往新矩阵中放入数据，col加一
* 一旦col等于c的话，则将之重置为0，然后row加一



**代码实现：**



```javascript
/**
 * @param {number[][]} nums
 * @param {number} r
 * @param {number} c
 * @return {number[][]}
 */
var matrixReshape = function(nums, r, c) {
    if(r*c === nums.length * nums[0].length){
        var arr = new Array(r);
        for(var m = 0; m < r; m++){
            arr[m] = [];
        }
        var row = 0;
        var col = 0;
        for(var i = 0; i < nums.length; i++){
            for(var j = 0; j < nums[i].length; j++){
                arr[row].push(nums[i][j]);
                col++;
                if(col == c){
                    col = 0;
                    row++;
                }
            }
        }
        return arr;
    }else{
        return nums;
    }
};
```

