---
title: 968. Binary Tree Cameras
weight: 3
bookToc: false
bookComments: true
---

# [968. Binary Tree Cameras](https://leetcode.com/problems/binary-tree-cameras/)

![Leetcode Hard](/images/leetcode_lvl_badges/hard.svg)

---

## Problem

You are given the root of a binary tree. We install cameras on the tree nodes where each camera at a
node can monitor its parent, itself, and its immediate children.

Return the minimum number of cameras needed to monitor all nodes of the tree.

### Example

#### Example 1:

Example 1:

![bst_cameras_01.png](https://assets.leetcode.com/uploads/2018/12/29/bst_cameras_01.png)

```jshelllanguage
Input: root = [0,0,null,0,0]
Output: 1
Explanation: One camera is enough to monitor all nodes if placed as shown.
```
#### Example 2:

![bst_cameras_02.png](https://assets.leetcode.com/uploads/2018/12/29/bst_cameras_02.png)

```jshelllanguage
Input: root = [0,0,null,0,null,0,null,null,0]
Output: 2 
Explanation: At least two cameras are needed to monitor all nodes of the tree. The above
image shows one of the valid configurations of camera placement.
```
### Constraints
- The number of nodes in the tree is in the range [1, 1000]. 
- Node.val == 0

### Follow up

---

## Complete Solution

```java
class Solution {

  int count;

  public int minCameraCover(TreeNode root) {
    this.count = 0;
    Boolean camReq = dfs(root);
    if (camReq != null && camReq) {
      this.count++;
    }
    return this.count;
  }

  /**
   * 1: Cam Not Required: null
   * 0: Cam Required: true
   * 2: Has Cam & Not Required: false
   */
  private Boolean dfs(TreeNode root) {
    if (root == null) {
      return null;
    }

    Boolean leftCamReq = dfs(root.left);
    Boolean rightCamReq = dfs(root.right);

    if ((leftCamReq != null && leftCamReq) || (rightCamReq != null && rightCamReq)) {
      count++;
      return false;
    } else if ((leftCamReq != null && !leftCamReq) || (rightCamReq != null && !rightCamReq)) {
      return null;
    } else {
      return true;
    }

  }

  private boolean isLeaf(TreeNode root) {
    return root != null && root.left == null && root.right == null;
  }
}
```

`Time Complexity`: {{< katex >}} O(n) {{< /katex >}}

`Space Complexity`: {{< katex >}} O(h) {{< /katex >}}