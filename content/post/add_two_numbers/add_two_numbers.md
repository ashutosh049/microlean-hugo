---
title: "Add two numbers"
description: "You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list"
date: 2020-08-31T13:09:42-06:00
draft: false
tags: ["DSA", "Leetcode", "Linked List"]
categories: ["Leetcode"]
GHissueID: 2
toc: false
series: ["Linked List"]
slug: "leetcode"
---

<h2><a href="https://leetcode.com/problems/add-two-numbers/">2. Add Two Numbers</a></h2><h3>Medium</h3><hr><div><p>You are given two <strong>non-empty</strong> linked lists representing two non-negative integers. The digits are stored in <strong>reverse order</strong>, and each of their nodes contains a single digit. Add the two numbers and return the sum&nbsp;as a linked list.</p>

<p>You may assume the two numbers do not contain any leading zero, except the number 0 itself.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

![add_two_numbers](/content/post/add_two_numbers/add_two_numbers_1.png)

<pre><strong>Input:</strong> l1 = [2,4,3], l2 = [5,6,4]
<strong>Output:</strong> [7,0,8]
<strong>Explanation:</strong> 342 + 465 = 807.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> l1 = [0], l2 = [0]
<strong>Output:</strong> [0]
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> l1 = [9,9,9,9,9,9,9], l2 = [9,9,9,9]
<strong>Output:</strong> [8,9,9,9,0,0,0,1]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li>The number of nodes in each linked list is in the range <code>[1, 100]</code>.</li>
	<li><code>0 &lt;= Node.val &lt;= 9</code></li>
	<li>It is guaranteed that the list represents a number that does not have leading zeros.</li>
</ul>
</div>

[comment]: <> ([Embed Title]&#40;https://youtu.be/8bh238ekw3 "@embed"&#41;)

#### Source codes
[add_two_numbers.java](/content/post/add_two_numbers/add_two_numbers.java "@embed")

```java
class Solution {
    public ListNode addTwoNumbers(ListNode node1, ListNode node2) {
        return addNode(node1, node2, 0);
    }
    
    ListNode addNode(ListNode node1, ListNode node2, int carry){
        
        if(node1 == null && node2 == null){
            if(carry > 0){
                return new ListNode(carry);                        
            }else {
                return null;
            }
        }
        
        ListNode out = new ListNode(carry);
        
        ListNode nextNode1 = null;
        ListNode nextNode2 = null;
        
        if(node1 != null){
            out.val += node1.val;
            nextNode1 = node1.next;
        }
        if(node2 != null){
            out.val += node2.val;
            nextNode2 = node2.next;
        }
        
        if(out.val > 9){
            int val = out.val;
            out.val = val % 10;
            carry = val / 10;
        }else{
            carry = 0;
        }
        
        out.next = addNode(nextNode1, nextNode2, carry);
        return out;
    }
    
}
```