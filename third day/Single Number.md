# Single Number



**题目：**



Given an array of integers, every element appears *twice* except for one. Find that single one.



**翻译：**



给予一个整数数组，除了一个元素之外，其余元素都会出现两次。找到那个一个的元素。



> 提示：你的算法应该有一个线性的时间复杂度。你可以在不使用额外的内存的情况下提升它吗？



**思路：**



> 首先，它要求算法是线性复杂度的，那么，时间复杂度的要求就是O(n)，一次遍历
>
> 之后，再了解一个规则——异或
>
> 相同整数异或：a⊕a = 0
>
> 0和任意一个数异或：a⊕0 = a



**代码实现：**



```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
var singleNumber = function(nums) {
    var res = 0;
    for(var item of nums){
        res ^= item;
    }
    return res;
};
```

