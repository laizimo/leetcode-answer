# Assign Cookies

**题目：**

Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie. Each child i has a greed factor gi, which is the minimum size of a cookie that the child will be content with; and each cookie j has a size sj. If sj >= gi, we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximize the number of your content children and output the maximum number.

**翻译：**

假设你是一个非常棒的父母，并且想要去给你的孩子一些饼干。但是，你只能给每一个孩子至多1块饼干。每个孩子i有一个贪婪因素gi，它指的是孩子将被满足的最小的饼干尺寸。并且每个饼干j有一个尺寸sj。如果sj大于等于gi，我们可以分配饼干j给孩子i，并且孩子i将被满足。你的目标是去最大化你可以满足的孩子的数量，然后输出这个最大化的数量。

**例子：**

```
Input: [1,2,3], [1,1]

Output: 1

Explanation: You have 3 children and 2 cookies. The greed factors of 3 children are 1, 2, 3. 
And even though you have 2 cookies, since their size is both 1, you could only make the child whose greed factor is 1 content.
You need to output 1.
```

```
Input: [1,2], [1,2,3]

Output: 2

Explanation: You have 2 children and 3 cookies. The greed factors of 2 children are 1, 2. 
You have 3 cookies and their sizes are big enough to gratify all of the children, 
You need to output 2.
```

**思路：**

* 首先，我们对孩子的欲望进行排序，也对饼干的尺寸进行排序
* 然后，遍历饼干，从小的欲望开始满足，这样才能保证数量的最大化

**代码实现：**

```javascript
/**
 * @param {number[]} g
 * @param {number[]} s
 * @return {number}
 */
var findContentChildren = function(g, s) {
    g.sort((item1, item2) => item1 - item2);
    s.sort((item1, item2) => item1 - item2);
    let count = 0;
    for(let i = 0, index = 0; i < s.length; i++){
        if(g[index] <= s[i]){
            count++;
            index++;
        }
    }
    return count;
};
```