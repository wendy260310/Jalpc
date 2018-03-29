---
layout: post
title:  "121. best time to buy and sell stock"
date:   2018-02-1 09:01:57 +0800
categories: leetcode 
---
The problem link is [problem 121][problem_121]
{% highlight ruby %}
Say you have an array for which the ith element is the price of a given stock
on day i.If you were only permitted to complete at most one transaction
(ie, buy one and sell one share of the stock), design an algorithm to find 
the maximum profit.
{% endhighlight %}
It is a [dp][dp_problem] problem,ret1 means max profite when selling on day i,ret2 is the result.This problem blow:
{% highlight ruby %}
gives you an array of int,find a consecutive sequence in the array,which has
the largest sum.
{% endhighlight %}
{% highlight ruby %}
public int maxProfit(int[] prices) {
	if (prices == null || prices.length <= 1)
		return 0;
	int ret1, ret2;
	ret1 = ret2 = prices[1] - prices[0];
	for (int i = 2; i < prices.length; ++i) {
		ret1 = ret1 > 0 ? (ret1 + prices[i] - prices[i - 1]) :
			(prices[i] - prices[i - 1]);
		if (ret2 < ret1)
			ret2 = ret1;
	}
	return ret2 > 0 ? ret2 : 0;
}
{% endhighlight %}
[problem_121]:https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/
[dp_problem]:https://en.wikipedia.org/wiki/Dynamic_programming
