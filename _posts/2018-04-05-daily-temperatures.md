---
layout: post
title:  "739. daily temperatures"
date:   2018-04-05
desc: leetcode 739 daily temperatures 
keywords: "leetcode,problem 739,algorithm"
categories: [Leetcode] 
icon: icon-html
tags: [leetcode,algorithm]
---
&emsp;&emsp;The problem link is [Daily Temperatures][problem_739].
```
Given a list of daily temperatures, produce a list that, for each day in the input, tells you how many days you would have to wait until a warmer temperature. If there is no future day for which this is possible, put 0 instead.
For example, given the list temperatures = [73, 74, 75, 71, 69, 72, 76, 73], your output should be [1, 1, 4, 2, 1, 1, 0, 0].
```
&emsp;&emsp;you can easily solve this problem in O^2.
```
public static int[] dailyTemperatures(int[] temperatures) {
	int[] ret = new int[temperatures.length];
	for (int i = 0; i < temperatures.length; ++i)
		for (int j = i + 1; j < temperatures.length; ++j) {
			if (temperatures[i] < temperatures[j]) {
				ret[i] = j - i;
				break;
			}
		}

	return ret;
}
```
&emsp;&emsp;But `O^2` algorithm is not enough. How to optimize this algorithm? Are there some connections between consecutive computes? When we want to compute `ret[i+1]`,can I use `ret[i]`? 
We know `ret[temperatures.length()-1]` is 0, So I decided to compute backward. If `ret[i] < ret [i+1]` then `ret[i] =1`, But If `ret[i] >=ret[i+1]`, how to find the first subsequent item which greater than
`ret[i]`? iterate? So I use a array to record the index of item which is the first subsequent item greater than current.I can find the first subsequent item greater than `ret[i]` recursively through this array. The recursive search may be O^n at worst case, But generally faster. 
```
public static int[] dailyTemperatures(int[] temperatures) {
	int[] ret = new int[temperatures.length], index = new int[temperatures.length];
	ret[temperatures.length - 1] = 0;
	index[temperatures.length - 1] = -1;

	for (int i = temperatures.length - 2; i >= 0; --i) {
		int tmp = i + 1, count = 0;
		while (tmp != -1 && temperatures[i] >= temperatures[tmp]) {
			count += ret[tmp];
			tmp = index[tmp];
		}
		if (tmp == -1) {
			index[i] = -1;
			ret[i] = 0;
		} else {
			ret[i] = count + 1;
			index[i] = tmp;
		}
	}
	return ret;
}
```



[problem_739]: https://leetcode.com/problems/daily-temperatures/description/

