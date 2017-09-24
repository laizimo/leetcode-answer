# Construct the Rectangle

**题目：**

For a web developer, it is very important to know how to design a web page's size. So, given a specific rectangular web page’s area, your job by now is to design a rectangular web page, whose length L and width W satisfy the following requirements:

```
1. The area of the rectangular web page you designed must equal to the given target area.

2. The width W should not be larger than the length L, which means L >= W.

3. The difference between length L and width W should be as small as possible.

```

You need to output the length L and the width W of the web page you designed in sequence.

**翻译：**

对于一个web开发者，去知道如何设计一个web页面的尺寸是非常重要的。因此，给一个具体的矩形web页面的面积。现在你的工作是去设计一个矩形web页面，它的长度L和宽度W满足以下要求：

1. 你设计的矩形网页的面积必须等于给予的目标面积
2. 宽度W不应该大于长度L，即L>=W
3. 长度L和宽度W之间的不同应该尽可能小

你需要输出web页面的长度L和宽度W

**例子：**

```
Input: 4
Output: [2, 2]
Explanation: The target area is 4, and all the possible ways to construct it are [1,4], [2,2], [4,1]. 
But according to requirement 2, [1,4] is illegal; according to requirement 3,  [4,1] is not optimal compared to [2,2]. So the length L is 2, and the width W is 2.
```

**思路：**

* 可以从1开始不断递增，知道变量的平方大于给定的面积
* 判断变量是否能够被面积整除，然后判断之间的距离
* 之后，将面积存放到res结果数组中

```javascript
/**
 * @param {number} area
 * @return {number[]}
 */
var constructRectangle = function(area) {
    const mid = Math.floor(Math.sqrt(area));
    const res = [];
    for(let i = mid; i >= 1; i--){
        if(area % i == 0){
            res.push(area / i);
            res.push(i);
            break;
        }
    }
    return res;
};
```

