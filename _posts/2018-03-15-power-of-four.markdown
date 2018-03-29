---
layout: post
title:  "342. power of four"
date:   2018-03-15 09:01:57 +0800
categories: [Leetcode] 
icon: icon-html
tags: [leetcode,algorithm]
---
The problem link is [Power Of Four][problem_342].
```
Given an integer (signed 32 bits), write a function to check whether it is
 a power of 4.
```
If `a` is power of 4, a or 0x55555554 equals 0x5555554.But not vice versa.So I first test if `a` is power of 2,means a only one `1` bit.
```
public static boolean isPowerOfFour(int num) {
	return num>=4 && ((num & (num - 1)) == 0) &&
		((num | 0x55555554) == 0x55555554);
}
```
[problem_342]:https://leetcode.com/problems/power-of-four/description/

