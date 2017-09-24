# Construct String from Binary Tree

**题目：**

You need to construct a string consists of parenthesis and integers from a binary tree with the preorder traversing way.

The null node needs to be represented by empty parenthesis pair "()". And you need to omit all the empty parenthesis pairs that don't affect the one-to-one mapping relationship between the string and the original binary tree.

**翻译：**

你需要使用预订的顺序去遍历二叉树，去组成一个由括号和整数构成的字符串

如果是空节点需要去使用空括号'()'代表。并且您需要省略不影响字符串和原始二叉树之间一对一映射关系的所有空括号对。

**例子：**

```
Input: Binary tree: [1,2,3,4]
       1
     /   \
    2     3
   /    
  4     

Output: "1(2(4))(3)"

Explanation: Originallay it needs to be "1(2(4)())(3()())", 
but you need to omit all the unnecessary empty parenthesis pairs. 
And it will be "1(2(4))(3)".
```

```
Input: Binary tree: [1,2,3,null,4]
       1
     /   \
    2     3
     \  
      4 

Output: "1(2()(4))(3)"

Explanation: Almost the same as the first example, 
except we can't omit the first parenthesis pair to break the one-to-one mapping relationship between the input and the output.
```

**思路：**

* 首先，我们使用递归的方式去遍历二叉树
* 如果节点是null，直接返回‘’；
* 如果节点存在，这首先加上节点的值
* 如果节点的左节点存在，则加入'('，并且递归左子树的节点，再加上')'；
* 如果节点的右节点存在，之后，如果右节点存在，而左节点不存在，那么应该去加上'()'，因为不能省略

**代码实现：**

```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} t
 * @return {string}
 */
var tree2str = function(t) {
    if(!t)
        return '';
    let str = '';
    str += t.val;
    if(t.left){
        str += '(';
        str += tree2str(t.left);
        str += ')';
    }
    if(t.right){
        if(!t.left){
            str += '()';
        }
        str += '(';
        str += tree2str(t.right);
        str += ')';
    }
    return str;
};
```

