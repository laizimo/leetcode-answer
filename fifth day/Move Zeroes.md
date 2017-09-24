# Move Zeroes

**题目：**

Given an array `nums`, write a function to move all `0`'s to the end of it while maintaining the relative order of the non-zero elements.

For example, given `nums = [0, 1, 0, 3, 12]`, after calling your function, `nums` should be `[1, 3, 12, 0, 0]`.

**翻译：**

给一个nums，写一个函数去移动所有0到nums的后面，而维持其他非0元素的相对的顺序

举个例子，给nums=[0，1，0，3，12]，之后调用你的函数，nums应该变成[1，3，12，0，0]

> 提示：
>
> 1. 你必须在nums中进行操作，没有通过复制另一个数组(即不能改变nums的引用)
> 2. 减少对nums的操作

**思路：**

* 我们可以设置两个变量i和index，其中i是循环的次数，遍历整个数组需要nums.length，而index是当前元素的下标
* 如果当前元素不为0，那么index往后移动一位
* 如果当前元素是0，将这个元素移除，然后把0添加到元素的末尾

**代码实现：**

```javascript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    let index = 0;
    for(let i = 0; i < nums.length; i++){
        if(nums[index] === 0){
            nums.splice(index, 1);
            nums.push(0);
        }else{
            index++;
        }
    }
};
```

