---
layout: post
title:  "461. Hamming Distance"
date:   2018-03-10 09:01:57 +0800
categories: [Leetcode] 
icon: icon-html
tags: [leetcode,algorithm]
---
The problem link is [Hamming Distance][problem_461].
```
The Hamming distance between two integers is the number of positions at which 
the corresponding bits are different.Given two integers x and y, calculate
the Hamming distance.
```
`xor` means if the corresponding bit is different,then we get a bit `1` else we get a bit `0`.We first `xor` x and y and then
count how many `1` bit in the result.

```
public static int hammingDistance(int x, int y) {
	int xor = x ^ y;
	int ret = 0;
	while (xor != 0) {
		ret++;
		xor &= (xor - 1);
	}
	return ret;
}
```
[problem_461]:https://leetcode.com/problems/hamming-distance/description/
