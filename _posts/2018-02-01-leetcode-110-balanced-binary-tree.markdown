---
layout: post
title:  "110. Balanced Binary Tree"
date:   2018-02-1 19:01:57 +0800
categories: [Leetcode] 
tags: [leetcode,algorithm]
desc: "leetcode 110 Balanced Binary Tree"
icon: icon-html
keywords: "leetcode,110"
---
The problem link is [problem 110][problem_110],we recursively call the method,returns a pair of data.1st indicates if it is a blance tree,2nd indicates its height.
a node is balanced if and only if its two children is balanced and two children's height diff less than 1.
```
public class Solution {

    public boolean isBalanced(TreeNode root) {
        return isBalancedHelper(root).getKey();
    }

    private AbstractMap.SimpleEntry<Boolean, Integer> isBalancedHelper(TreeNode root) {
        if (root == null)
            return new AbstractMap.SimpleEntry(true, 0);

        AbstractMap.SimpleEntry<Boolean, Integer> left = isBalancedHelper(root.left);
        AbstractMap.SimpleEntry<Boolean, Integer> right = isBalancedHelper(root.right);

        if (left.getKey() && right.getKey()
                && Math.abs(left.getValue().intValue() - right.getValue().intValue()) <= 1) {
            return new AbstractMap.SimpleEntry<>(true,
                    left.getValue().intValue() > right.getValue().intValue() ? left.getValue() + 1 :
                            right.getValue() + 1);
        }

        return new AbstractMap.SimpleEntry<>(false, 0);

    }
}
```
[problem_110]:https://leetcode.com/problems/balanced-binary-tree/description/
