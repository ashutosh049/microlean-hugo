---
title: 144. Binary Tree Preorder Traversal
weight: 3 
bookToc: true
bookComments: true
draft: false
bookHidden: false
---

 # [144. Binary Tree Preorder Traversal](https://leetcode.com/problems/binary-tree-preorder-traversal)
![Leetcode Easy](/images/leetcode_lvl_badges/easy.svg)

---

## Problem
Given the root of a binary tree, return the preorder traversal of its nodes' values.
### Example
#### Example 1:
![inorder_1.jpg](https://assets.leetcode.com/uploads/2020/09/15/inorder_1.jpg)

Input: root = [1,null,2,3]

Output: [1,2,3]
### Constraints
- The number of nodes in the tree is in the range [0, 100]. 
- 100 <= Node.val <= 100
### Follow up
Recursive solution is trivial, could you do it iteratively?

---

## Approach and Intuition

### Recursive approach

{{< tabs "binary-tree-preorder-traversal_recursive" >}}
{{< tab "Java" >}}
```Java
class Solution {
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        helper(root, res);
        return res;
    }

    public void helper(TreeNode root, List<Integer> res) {
        if (root != null) {
            res.add(root.val);
            helper(root.left, res);
            helper(root.right, res);
        }
    }
}
```

{{< /tab >}}
{{< tab "C++" >}}  {{< /tab >}}
{{< tab "Python" >}}  {{< /tab >}}
{{< tab "Javascript" >}}  {{< /tab >}}
{{< /tabs >}}

#### Complexity Analysis

`Time complexity`: {{< katex >}} O(n) {{< /katex >}} as the recurrence relation is {{< katex >}} T(n) = 2T(n/2) + 1 {{< /katex >}}.

###### Explanation

Recurrence Relation:

Let {{< katex >}}T(n){{< /katex >}} is the number of operations executed in your traversal algorithm(DFS). Function is recursively called 2 times each time for left and right sub-tree. 

{{< katex >}}
T(n) = 2T(n/2) + 1
{{< /katex >}}.

Using the [Masters' Theorem](https://en.wikipedia.org/wiki/Master_theorem_(analysis_of_algorithms)) , we have 
<br>
{{< katex >}}T(n) = a*T(n/b) + f(n){{< /katex >}}

<br>`f(n)` is some constant.

For a Graph, the complexity of a Depth First Traversal is {{< katex >}} O(V + E) {{< /katex >}},
where `V` is the number of nodes or vertices, and `E` is the number of edges.

A `Binary Tree` is also a `Graph`, and we visit **each node only once**.

The complexity of each of these Depth-first traversals(Pre, In and Post) is {{< katex >}}O(V + E){{< /katex >}}
or {{< katex >}}O(N + E){{< /katex >}}.

Since the number of edges that can originate from a node is limited to 2 in the case of a `Binary Tree`,
the maximum number of edges in a `Binary Tree` is {{< katex >}}n-1{{< /katex >}}, where `n` is the total number of nodes.

The complexity then becomes {{< katex >}}O(n + n-1){{< /katex >}}, which is {{< katex >}}O(n){{< /katex >}}.

> As for recursion, the only difference is that recursive method calls build the stack implicitly by pushing call frames to the JVM stack

##### Master Theorem

Let {{< katex >}}T(n){{< /katex >}} be a monotonically increasing function that satisfies:
<br>
<br>
{{< katex >}}T(n) = a T(n/b) + f(n){{< /katex >}}
<br>
{{< katex >}}T(1) = c{{< /katex >}}
<br>
<br>
where {{< katex >}}a >= 1, b >= 2, c>0{{< /katex >}}.
<br>
<br>
If {{< katex >}}f(n){{< /katex >}} is {{< katex >}}\Theta(n^d){{< /katex >}} where {{< katex >}}d >= 0{{< /katex >}}
<br>
then
<br>
<br>
{{< katex >}}
x = \begin{cases}
a &\text{if } b \\
c &\text{if } d
\end{cases}
{{< /katex >}}

`Space Complexity`: {{< katex >}} O(1) {{< /katex >}}



---

### Iterative

---