# Best Time to Buy and Sell Stock II - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/description/)

Say you have an array for which the ith element is the price of a given stock on day i.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).

# Solution
```java
class Solution {
    public int maxProfit(int[] prices) {
        if (prices == null) return 0;
        
        int profit = 0;
        for (int i = 1; i < prices.length; i++){
            if (prices[i] > prices[i-1])
                profit += prices[i] - prices[i-1];
        }
        return profit;
    }
}
```
## Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)