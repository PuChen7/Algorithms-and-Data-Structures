# Best Time to Buy and Sell Stock with Transaction Fee - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-with-transaction-fee/description/)

Your are given an array of integers prices, for which the i-th element is the price of a given stock on day i; and a non-negative integer fee representing a transaction fee.

You may complete as many transactions as you like, but you need to pay the transaction fee for each transaction. You may not buy more than 1 share of a stock at a time (ie. you must sell the stock share before you buy again.)

Return the maximum profit you can make.

# Solution
```java
class Solution {
    public int maxProfit(int[] prices, int fee) {
        int cash = 0, hold = -prices[0];
        for (int i = 1; i < prices.length; i++){
            cash = Math.max(cash, hold+prices[i]-fee);
            hold = Math.max(hold, cash-prices[i]);
        }
        return cash;
    }
}
```
# Complexity
* Time Complexity: O(n)
* Space Complexity: O(1)