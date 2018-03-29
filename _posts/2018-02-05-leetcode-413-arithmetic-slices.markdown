---
layout: post
title:  "413. Arithmetic Slices"
date:   2018-02-5 09:01:57 +0800
categories: leetcode 
---
The problem link is [problem 413][problem_413]

{% highlight ruby %}
A sequence of number is called arithmetic if it consists of at least three
elements and if the difference between any two consecutive elements is
the same.
A zero-indexed array A consisting of N numbers is given. A slice of 
that array is any pair of integers (P, Q) such that 0 <= P < Q < N.
A slice (P, Q) of array A is called arithmetic if the sequence:
A[P], A[p + 1], ..., A[Q - 1], A[Q] is arithmetic. In particular, 
this means that P + 1 < Q.The function should return the number of 
arithmetic slices in the array A.
{% endhighlight %}
We should first find some longest consecutive sequences,for a given array,it may contains some such sequences,for example [1,2,3,4,6,8,10],
We can get two longest consecutive sequence,[1,2,3,4] and [4,6,8,10].For a longest consecutive sequence longer than 3(length is n ),we
can get (n-1)\*(n-2)/2 arithmetic subsequence(1+2+....+n-2).
{% highlight ruby %}
public static int numberOfArithmeticSlices(int[] A) {
	if (A == null || A.length < 3)
		return 0;
	int ret = 0, diff = Integer.MAX_VALUE, consecutiveLength = 2;
	for (int i = 1; i < A.length; ++i) {
		if ((A[i] - A[i - 1]) != diff) {
			if (consecutiveLength >= 3)
				ret += (consecutiveLength - 2) * (consecutiveLength - 1) / 2;
			consecutiveLength = 2;
			diff = A[i] - A[i - 1];
		} else {
			consecutiveLength++;
		}
	}
	if (consecutiveLength >= 3)
		ret += (consecutiveLength - 1) * (consecutiveLength - 2) / 2;

	return ret;
}
{% endhighlight %}
[problem_413]:https://leetcode.com/problems/arithmetic-slices/description/
