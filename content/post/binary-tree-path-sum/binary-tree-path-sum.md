---
title: "Binary Tree path sum"
description: "Binary Tree Path Sum Iterative Post Order approach and explanation"
date: 2020-08-31T13:09:42-06:00
draft: false
tags: ["Java", "DSA", "Leetcode", "Binary Tree", "Tree Traversal"]
categories: ["Leetcode"]
GHissueID: 2
toc: false
#series: ["Binary Tree"]
series: Binary Tree
#slug: "leetcode"
---

You can refer to the Leetcode problem [112. Path Sum](https://leetcode.com/problems/path-sum/)

#### Problem Statement
Given the `root` of a binary tree and an integer `targetSum`, return `true` if the tree has a *root-to-leaf* path such that adding up all the values along the path equals `targetSum`.

> A leaf is a node with no children.



Example 1:

![binary-tree-path-sum](/content/post/binary-tree-path-sum/binary-tree-path-sum.png)

Input:
`root` = [5,4,8,11,null,13,4,7,2,null,null,null,1], `targetSum` = 22

Output: `true`
`Explanation`: The root-to-leaf path with the target sum is shown.


---

### Post Order and path sum

`Iterative`

#### Intuition

Proceed in a classic [binary-tree-postorder-traversal](https://leetcode.com/problems/binary-tree-postorder-traversal) iterative fashion, with following 2 things in mind:

1. Keep a `currSum` variable which will have the total sum added up to `curr` node.
2. On each pop-operation/climb-up (processing of a node), and since we know that we have already checked if this node was a `leaf` node and if the `currSum` till this node is equal to `target`, we reduce it's value from `currSum` which we added while traversing downwards.

While you descend and go on adding the node values, on traversing up, we need to discard added sum of those nodes.

#### Example
`Input`: [1,-2,-3,1,3,-2,null,-1]
`targetSum`: 2

![image](/content/post/binary-tree-path-sum/binary-tree-path-sum-example-1.png)

Steps/Dry run :
1. We declared a `currSum` variable to hold our total sum till current node
2.  We kept a `pre` reference variable which will point to a previous node that has been last popped-out or last processed. This will help us not to re-process the right child.
3. We start scanning from `root` node and till we reach a left-most node, for each node, do
    - Add `curr.val` to `currSum`
    - push the `curr` node onto stack `s`
    - traverse to left child
4. When the inner while loop ends, our `curr` would be pointing to `null` (left-child of the left-most node, this left-most node would always be the leaf node).
5. Our `curr` is `null`, there is nothing to go left now, start looking into our stack
6. peek from stack i.e. `curr = s.peek`. Remember, we are doing a `post-order` traversal, so we need to descend right from this peeked node, and hence is the `peek` operation, we can not just `pop` from stack.
7. The very first `peek` from stack would give us the left-most node(a leaf node). This is not important, but the point is at this point, we start climbing up.
8. Check if this node meets our criteria of a leaf node with sum till this equals to `target`.
    - If `yes`, we are done with the whole process, no need to scan further and we can just break from this point.
10. If the flow continues i.e. even if it was a leaf node but the sum till this node is not what we are looing for, start popping out.
11. We only pop(post-order) if any of following 2 conditions are met
    - If there is no right-child
    - If we already processed the right child(right child is equal/point to `pre`)
13. If the above condition is true, and pop the current node, do following:
    - Decrease the `currSum` as `currSum -= curr.val`. (We need to revert what we added to our `currSum`)
    - point `pre` to this `curr` node.
    - point `curr` to `null`
14. If we have not processed the right child, descend to right child. (and the loop again begins with this  right child as new `curr` and will look for the left most node of this `curr` and go on adding the values to `currSum`.)

So, in above example, once we are done verifying node `g`(it's a leaf node and currSum != targetSum), we shall be climbing up to node `d`  then `b` and then to a leaf node `e`. While climbing up from `g` -> `d` -> `b` -> `e`, we descrease the corresponding values of node `g` and `d`. Note that we are not decreasing the value of `b` as we are not yet done with right child `e`.

In case our currSum would have been `-2`, then node `e` would not meet our criteria and we would be descreasing the values of node `e` and `b` also.


Time   : `O(n)`
Space : `O(n`

#### program

```java
private boolean hasPathSum_iterative(TreeNode root, int targetSum){
        
        boolean hasPath = false;
        
        if(root == null)
            return hasPath;
        
        TreeNode curr = root;
        TreeNode pre = null;
        int currSum = 0;
        Stack<TreeNode> s = new Stack();
        
        while(curr != null || !s.isEmpty()){
            
            while(curr != null){
                currSum += curr.val;
                s.push(curr);
                curr = curr.left;
            }
            
            curr = s.peek();

            if(curr.left == null && curr.right == null && currSum == targetSum){
                hasPath = true;
                break;
            }
            
            // If right ST is null or already processed(equal to pre)
            // then process curr
            if(curr.right == null || curr.right == pre){
                curr = s.pop();
                currSum -= curr.val;
                pre = curr;
                curr = null;   
            }else {
                curr = curr.right;
            }
            
            
        }
        
        return hasPath;
    }
```

Hope this might have help you to understand the concept of iterative `post order` and apply extra logic to solve the `path-sum` problem.

Indeed, there are various other approaches to do the same, I wrote this to make someone relate idea behind post-order and sum.

See also [binary-tree-postorder-traversal](https://leetcode.com/problems/binary-tree-postorder-traversal)

PS: Stay tuned for more such problem explanation and approaches
