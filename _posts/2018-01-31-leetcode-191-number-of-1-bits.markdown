---
layout: post
title:  "191. number of 1 bits"
date:   2018-01-31 
desc: leetcode 191 number of 1 bits
categories: [Leetcode] 
icon: icon-html
tags: [Jalpc,Jekyll]
---
The problem link is [problem 191][problem_191]
```
Write a function that takes an unsigned integer and returns the number of '1'
bits it has(also known as the Hamming weight).For example, the 32-bit integer
'11' has binary representation 00000000000000000000000000001011, so the
function should return 3.
```
We can use `n&(n-1)` to test if a int is power of 2,`n&=(n-1)` will remove the lowest 1 bit.
```
public  int hammingWeight(int n) {
	int ret = 0;
	while (n != 0) {
            n &= n - 1;
            ret++;
        }
        return ret;
}
```
[problem_191]:https://leetcode.com/problems/number-of-1-bits/description/
