---
layout: post
title:  "724. find pivot index "
date:   2018-04-02 
desc: "leetcode 724 find pivot index" 
keywords: "leetcode,problem 724,find pivot index"
categories: [Leetcode] 
icon: icon-html
tags: [leetcode,algorithm]
---
The description of the problem goes [here][problem_724]
```
Given an array of integers nums, write a method that returns the "pivot" index of this array.
We define the pivot index as the index where the sum of the numbers to the left of the index is equal to the sum of the numbers to the 
right of the index.If no such index exists, we should return -1. If there are multiple pivot indexes, you should return the left-most
pivot index.
```
`left`-`index`-`right`,`left`*2+`index`=`sum`.
```
public  int pivotIndex(int[] nums) {
	int sum = Arrays.stream(nums).sum(), ret = 0;
	for (int i = 0; i < nums.length; ++i) {
		if (ret * 2 + nums[i] == sum)
			return i;
		ret += nums[i];
	}
	return -1;
}
```
[problem_724]: https://leetcode.com/problems/find-pivot-index/description/
