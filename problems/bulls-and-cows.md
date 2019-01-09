# Bulls and Cows - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/bulls-and-cows/)

You are playing the following Bulls and Cows game with your friend: You write down a number and ask your friend to guess what the number is. Each time your friend makes a guess, you provide a hint that indicates how many digits in said guess match your secret number exactly in both digit and position (called "bulls") and how many digits match the secret number but locate in the wrong position (called "cows"). Your friend will use successive guesses and hints to eventually derive the secret number.

Write a function to return a hint according to the secret number and friend's guess, use A to indicate the bulls and B to indicate the cows. 

Please note that both secret number and friend's guess may contain duplicate digits.

```java
class Solution {
    public String getHint(String secret, String guess) {
        int cow = 0, bull = 0;
        int[] index = new int[10]; // single digit wont't exceed
        
        for (int i = 0; i < secret.length(); i++){
            int c1 = Character.getNumericValue(secret.charAt(i));
            int c2 = Character.getNumericValue(guess.charAt(i));
            
            if (c1 == c2) bull++;
            else {
                if (index[c1] < 0) cow++;
                if (index[c2] > 0) cow++;
                index[c1]++;
                index[c2]--;
            }
        }    
        return bull+"A"+cow+"B";
    }
}
```
