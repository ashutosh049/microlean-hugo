---
title: 257. Binary Tree Paths
weight: 3
bookToc: false
bookComments: true
---

<h2><a href="https://leetcode.com/problems/binary-tree-paths/">257. Binary Tree Paths</a></h2>

![Leetcode Easy](/images/leetcode_lvl_badges/easy.svg)

<hr><div><p>Given the <code>root</code> of a binary tree, return <em>all root-to-leaf paths
in <strong>any order</strong></em>.</p>

<p>A <strong>leaf</strong> is a node with no children.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2021/03/12/paths-tree.jpg" style="width: 207px; height: 293px;">
<pre><strong>Input:</strong> root = [1,2,3,null,5]
<strong>Output:</strong> ["1-&gt;2-&gt;5","1-&gt;3"]
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> root = [1]
<strong>Output:</strong> ["1"]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in the tree is in the range <code>[1, 100]</code>.</li>
	<li><code>-100 &lt;= Node.val &lt;= 100</code></li>
</ul>
</div>


### program

{{< tabs "binary-tree-paths" >}}
{{< tab "Java" >}}  
```java
class Solution {
    List<String> res;
    public List<String> binaryTreePaths(TreeNode root) {
       
        //return binaryTreePaths_dfs_iterative(root);
        
        this.res=new ArrayList<String>();
        binaryTreePaths_dfs_recursive(root, new StringBuilder());
        return this.res;
        
    }
    
    public List<String> binaryTreePaths_dfs_iterative(TreeNode root) {
        
        List<String> out = new ArrayList<>();
        
        if(root == null)
            return out;
        
        Deque<TreeNode> nodeStack = new ArrayDeque<>();
        TreeNode curr = root;
        TreeNode pre = null;
        StringBuilder sb = new StringBuilder();
        
        while(curr != null || !nodeStack.isEmpty()){
            if(curr != null){
                if(sb.length() > 0){
                    sb.append("->");
                }
                sb.append(curr.val);
                nodeStack.push(curr);
                curr = curr.left;
            }else{
                curr = nodeStack.peek();
                
                // if leaf node
                if(curr.left == null && curr.right == null){
                    out.add(sb.toString());
                }
                
                if(curr.right == null || curr.right == pre){
                    curr = nodeStack.pop();
                    
                    int currAppendedStringLength = String.valueOf(curr.val).length();
                    

                    if(sb.lastIndexOf("->") > -1){
                        currAppendedStringLength +=2 ;
                    }
                        sb.delete(sb.length()-currAppendedStringLength, sb.length());
                    
                    pre = curr;
                    curr = null;
                }else{
                    curr= curr.right;
                }
            }
        }
        return out;
    }
    
    public void binaryTreePaths_dfs_recursive(TreeNode root, StringBuilder pathBuilder) {
        
        if(root == null){
            return;
        }
        
        
        if(pathBuilder.length() >= 1){
            pathBuilder.append("->");
        }
        pathBuilder.append(root.val);
        
        
        binaryTreePaths_dfs_recursive(root.left, new StringBuilder(pathBuilder.toString()));
        binaryTreePaths_dfs_recursive(root.right, new StringBuilder(pathBuilder.toString()));
        
        if(root.left == null && root.right == null){
            this.res.add(pathBuilder.toString());
        }
        
        
    }
}
```
{{< /tab >}}
{{< tab "C++" >}}  {{< /tab >}}
{{< tab "Python" >}}  {{< /tab >}}
{{< tab "Javascript" >}}  {{< /tab >}}
{{< /tabs >}}
