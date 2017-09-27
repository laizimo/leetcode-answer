# Minimum Index Sum of Two Lists

**题目：**

Suppose Andy and Doris want to choose a restaurant for dinner, and they both have a list of favorite restaurants represented by strings.

You need to help them find out their common interest with the least list index sum. If there is a choice tie between answers, output all of them with no order requirement. You could assume there always exists an answer.

**翻译：**

假定Andy和Doris想要选择一个吃晚餐的饭店，并且他们都有一个最喜欢的通过字符串代替的餐厅的列表。

你需要使用最小列表索引和去帮助他们找出他们共同的兴趣。如果答案之间存在选择，没有顺序要求，输出所有的这些。你可以假定那里一定存在一个答案

**例子：**

```
Input:
["Shogun", "Tapioca Express", "Burger King", "KFC"]
["Piatti", "The Grill at Torrey Pines", "Hungry Hunter Steakhouse", "Shogun"]
Output: ["Shogun"]
Explanation: The only restaurant they both like is "Shogun".
```

```
Input:
["Shogun", "Tapioca Express", "Burger King", "KFC"]
["KFC", "Shogun", "Burger King"]
Output: ["Shogun"]
Explanation: The restaurant they both like and have the least index sum is "Shogun" with index sum 1 (0+1).
```

**思路：**

* 首先使用map将list2数组中的字符窜，根据它的值-下标的形式记录下来
* 然后遍历list2，去判断当前元素在map中存不存在
* 如果存在，则判断取出的值和当前元素的下标之和与之前记录的总和之间的大小
* 如果大于之前记录的总和的话，重新定义结果数组，将当前元素放入数组中，然后将这个值替换之前记录的值
* 如果等于的话，就将结果放入结果数组

**代码实现：**

```javascript
/**
 * @param {string[]} list1
 * @param {string[]} list2
 * @return {string[]}
 */
var findRestaurant = function(list1, list2) {
    const map = new Map();
    let sum = 9999;
    let res;
    for(let i = 0; i < list1.length; i++){
        map.set(list1[i], i);
    }
    for(let i = 0; i < list2.length; i++){
        if(map.has(list2[i])){
            let index = map.get(list2[i]);
            if(sum > index + i){
                sum = index + i;
                res = [list2[i]];
            }else if(sum === index + i){
                res.push(list2[i]);
            }
        }
    }
    return res;
};
```