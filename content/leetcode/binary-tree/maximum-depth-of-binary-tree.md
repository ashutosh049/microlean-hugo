---
title: 104. Maximum Depth of Binary Tree
weight: 3
bookToc: true
bookComments: true
---

# [104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)
![Leetcode Easy](/images/leetcode_lvl_badges/easy.svg)

---

## Problem
Given the root of a binary tree, return its maximum depth.

> A binary tree's maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

### Example

#### Example 1:
```
    (3)
 /      \
(9)     (20)
       /    \
    (15)     (7)
```


Input: root = `[3,9,20,null,null,15,7]`
Output: `3`

### Constraints
1. The number of nodes in the tree is in the range [0, 104]. 
2. {{< katex >}} -100 <= Node.val <= 100 {{< /katex >}}
### Follow up

---

## Approach and Intuition

### 1. Recursive traversal

```java
 private int maxDepth_Recursive(TreeNode root){
   if(root == null) return 0;
    return Math.max(maxDepth(root.left), maxDepth(root.right)) +1;
 }
```

`Time Complexity`: {{< katex >}} O(n) {{< /katex >}}

`Space Complexity`: {{< katex >}} O(n) {{< /katex >}}

### 2. Iterative BFS

We can use BFS to get the highest level(deepest node). Implement BFS, return the size of the List of level nodes.

Check this question for more into on [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/http://)

```java
private int maxDepth_Iterative_BFS(TreeNode root){
	
	List<List<Integer>> resultList = new ArrayList<>();
	
	 if(root == null) return 0;
	
	TreeNode curr = root;
	
	Queue<TreeNode> q = new LinkedList<>();
	
	q.offer(curr);
	
	while(!q.isEmpty()){
		int qSize = q.size();
		List<Integer> subList = new ArrayList<>();
		
		for(int i=0; i< qSize; i++){
			curr = q.poll();
			
			subList.add(curr.val);
			
			if(curr.left != null){
				q.offer(curr.left);
			}
			
			if(curr.right != null){
				q.offer(curr.right);
			}
		}
		//add to main list
		resultList.add(subList);
		
	}
	
	return resultList.size();
	
}
```

`Time Complexity`: {{< katex >}} O(n) {{< /katex >}}

`Space Complexity`: {{< katex >}} O(n) {{< /katex >}}

### 3. Iterative traversal using height variable

```java
private int maxDepth_usingHeightVariable(TreeNode root){
        
	 if(root == null) return 0;
	
	Queue<TreeNode> q = new LinkedList<>();
	
	q.offer(root);
	int maxDepth = 0;
	
	while(!q.isEmpty()){
		
		maxDepth++;
		int i = q.size();
		while(i-- > 0){
			
		 TreeNode curr = q.poll();

		 if(curr.left != null){
			q.offer(curr.left);
		 }

		 if(curr.right != null){
			q.offer(curr.right);
		 }
		}
		
	}
	return maxDepth;
}
```

`Time Complexity`: {{< katex >}} O(n) {{< /katex >}}

`Space Complexity`: {{< katex >}} O(n) {{< /katex >}}

---

## Related problems
1. [102. Binary Tree Level Order Traversal](https://leetcode.com/problems/binary-tree-level-order-traversal/solution/)
2. [987. Vertical Order Traversal of a Binary Tree](https://leetcode.com/problems/vertical-order-traversal-of-a-binary-tree/)
3. [199. Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/)
4. [107. Binary Tree Level Order Traversal II](https://leetcode.com/problems/binary-tree-level-order-traversal-ii/)
5. [94. Binary Tree Inorder Traversal](https://leetcode.com/problems/binary-tree-inorder-traversal/)

{{< columns >}}
<--->
<--->
{{< button relref="/balanced_binary_tree" >}} 110. Balanced Binary Tree {{< fontawesome "solid/circle-arrow-right" >}} {{< /button >}}
{{< /columns >}}

---