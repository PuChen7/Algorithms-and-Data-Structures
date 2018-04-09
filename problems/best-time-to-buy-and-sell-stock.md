# Best Time to Buy and Sell Stock - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)

Say you have an array for which the ith element is the price of a given stock on day i.

If you were only permitted to complete at most one transaction (ie, buy one and sell one share of the stock), design an algorithm to find the maximum profit.

## My Solution - Version I
```java
class Solution {
    public int maxProfit(int[] prices) {        
        int profit = 0;
        int min = Integer.MAX_VALUE;
        for (int i = 0; i < prices.length; i++){
            if (prices[i] < min)
                min = prices[i];
            else if (prices[i] - min > profit)
                profit = prices[i] - min;
        }
        return profit;
    }
}
```

Time Complexity: O(n)
