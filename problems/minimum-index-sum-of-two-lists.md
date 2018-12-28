# Minimum Index Sum Of Two Lists - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/minimum-index-sum-of-two-lists/)

 Suppose Andy and Doris want to choose a restaurant for dinner, and they both have a list of favorite restaurants represented by strings.

You need to help them find out their common interest with the least list index sum. If there is a choice tie between answers, output all of them with no order requirement. You could assume there always exists an answer.

Example 1:

Input:
["Shogun", "Tapioca Express", "Burger King", "KFC"]

["Piatti", "The Grill at Torrey Pines", "Hungry Hunter Steakhouse", "Shogun"]

Output: ["Shogun"]

Explanation: The only restaurant they both like is "Shogun".

## Solution
```java
class Solution {
    public String[] findRestaurant(String[] list1, String[] list2) {
        HashMap<String, Integer> map1 = new HashMap<>();
        List<String> res = new LinkedList<>();
        
        for (int i = 0; i < list1.length; i++) 
            map1.put(list1[i], map1.getOrDefault(list1[i], i));
        
        int sum = Integer.MAX_VALUE;
        for (int i = 0; i < list2.length; i++){
                if (map1.get(list2[i]) != null && sum >= map1.get(list2[i]) + i){
                    if (sum > map1.get(list2[i]) + i){
                        res.clear();
                        sum = map1.get(list2[i]) + i;
                    }
                    res.add(list2[i]);
                }
        }
        return res.toArray(new String[0]);
    }
}
```
