# Merge Two Binary Tree

**题目：**



Given two binary trees and imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not. 

You need to merge them into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of new tree.



**翻译：**



给两个二叉树和当你将它们其中之一去覆盖另一个的图像，两个数的某些节点被重叠，而另外的节点不会被重叠



你需要去将它们合并到一颗新的二叉树。合并的规则是如果两个节点重叠，那么将两个节点的值相加来作为新合并节点的值。否则，非空的节点将被使用到新树上。



**例子：**



```
Input: 
	Tree 1                     Tree 2                  
          1                         2                             
         / \                       / \                            
        3   2                     1   3                        
       /                           \   \                      
      5                             4   7                  
Output: 
Merged tree:
	     3
	    / \
	   4   5
	  / \   \ 
	 5   4   7
```





**思路解析：**



题目是一个二叉树的合并，使用递归来做是最简单的，折叠的两个节点值相加，然后不折叠的值则返回另个



# 代码步骤

* 判断t1节点是否为空，为空则返回t2的树内容
* 判断t2节点是否为空，为空则返回t1的树内容
* t1的值加上t2的值，赋值t1
* 递归传入t1的左子树和t2的左子树
* 递归传入t1的右子树和t2的右子树



```javascript
/**
*function TreeNode(val){
*  this.val = val;
*  this.left = this.right = null;
*}
*
*@param {TreeNode, TreeNode} t1, t2
*@return {TreeNode}
*/
function mergeTrees(t1, t2){
    if(!t1)
      return t2;
    if(!t2)
      return t1;
  	
    t1.left = mergeTrees(t1.left, t2.left);
    t1.val += t2.val;
    t1.right = mergeTrees(t1.right, t2.right);
    return t1;
}
```

