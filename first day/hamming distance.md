1. 海明距离(Hamming distance)

    **题目：**The Hamming distance between two integers is the number of positions at which the corresponding bits are different.Given two integers x and y, calculate the Hamming distance.

    **翻译：**两个整数之间的海明距离是在相应的位不同的位置数目。给两个整数x和y，计算海明距离

    **例子：**

    ```
    Input: x = 1, y = 4

    Output: 2

    Explanation:
    1   (0 0 0 1)
    4   (0 1 0 0)
           ↑   ↑

    The above arrows point to positions where the corresponding bits are different.
    ```

    ​

    [题目链接](https://leetcode.com/problems/hamming-distance/description/)

    思路解析：可以通过将两个整数异或，然后计算二进制中的1的数目，即是海明距离。

    > 位操作符详解：
    > &：按位与   |：按位或    ^：按位异或    >>：右移，相当于除2     >>：左移，相当于除3

## 代码步骤：

* 将x与y进行异或，新数w
* 循环w，直到为w等于0
  * 循环中w与1按位与，判断最后一位是否为整数
  * 将w进行右移操作
* 返回计数值



```javascript
/**
* @param {number} x
* @param {number} y
* @return {number}
*/
var hammingDistance = function (x, y) {
    var w = x ^ y;
  	var count = 0;
  	while(w){
        if(w & 1){
            count++;
        }
      	w >>= 1;
    }
  	return w
}
```

