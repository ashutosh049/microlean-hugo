---
title: 110. Balanced Binary Tree
weight: 3
bookToc: false
bookComments: true
---

<h2><a href="https://leetcode.com/problems/balanced-binary-tree/">110. Balanced Binary Tree</a></h2><h3>Easy</h3><hr><div><p>Given a binary tree, determine if it is height-balanced.</p>

<p>For this problem, a height-balanced binary tree is defined as:</p>

<blockquote>
<p>a binary tree in which the left and right subtrees of <em>every</em> node differ in height by no more than 1.</p>
</blockquote>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/06/balance_1.jpg" style="width: 342px; height: 221px;">
<pre><strong>Input:</strong> root = [3,9,20,null,null,15,7]
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/10/06/balance_2.jpg" style="width: 452px; height: 301px;">
<pre><strong>Input:</strong> root = [1,2,2,3,3,null,null,4,4]
<strong>Output:</strong> false
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> root = []
<strong>Output:</strong> true
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[0, 5000]</code>.</li>
	<li><code>-10<sup>4</sup> &lt;= Node.val &lt;= 10<sup>4</sup></code></li>
</ul>
</div>

### Approach
```java
class Solution {
    public boolean isBalanced(TreeNode root) {
        return getHeight(root) != -1;
    }
    
    private int getHeight(TreeNode root){
        
        if(root == null){
            return 0;
        }
        
        int heightLeftSt = getHeight(root.left);
        // can be further improved by: before recursing right, check if left is already imbalanced.
        int heightRightSt = heightLeftSt != -1 ? getHeight(root.right) : -1;
    
        // if(heightLeftSt == -1 || heightRightSt == -1 || Math.abs(heightLeftSt - heightRightSt) > 1){
        //     return -1;
        // }
        
        if(heightRightSt == -1 || Math.abs(heightLeftSt - heightRightSt) > 1){
            return -1;
        }

        return Math.max(heightLeftSt, heightRightSt) +1;
                 
    }
}
```

{{< columns >}}

{{< button relref="/maximum-depth-of-binary-tree" >}} {{< fontawesome "solid/circle-arrow-left" >}} 104. Maximum Depth of Binary Tree {{< /button >}}
<--->
<--->
{{< button relref="/binary_search_tree_iterator" >}} 173. Binary Search Tree Iterator {{< fontawesome "solid/circle-arrow-right" >}} {{< /button >}}
{{< /columns >}}

---
