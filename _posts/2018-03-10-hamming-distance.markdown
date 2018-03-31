---
layout: post
title:  "461. Hamming Distance"
desc: "leetcode Hamming Distance"
keywords: "leetcode,Hamming Distance"
date:   2018-03-10 09:01:57 +0800
categories: [Leetcode] 
icon: icon-html
tags: [leetcode,Hamming Distance]
---
The problem link is [Hamming Distance][problem_461].
```
The Hamming distance between two integers is the number of positions at which 
the corresponding bits are different.Given two integers x and y, calculate
the Hamming distance.
```
`xor` means if the corresponding bit is different,then we get a bit `1` else we get a bit `0`.We first `xor` x and y and then
count how many `1` bit in the result. You can find more [Bit Twiddling Hacks][bit_twiddling_hacks].
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
[bit_twiddling_hacks]: https://graphics.stanford.edu/~seander/bithacks.html#RoundUpPowerOf2
