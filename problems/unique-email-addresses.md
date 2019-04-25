# Unique Email Addresses - from [LeetCode](https://leetcode.com)
[View this problem on LeetCode](https://leetcode.com/problems/unique-email-addresses/)

## Description
Given a list of emails, we send one email to each address in the list.  How many different addresses actually receive mails? 

## Thinking & Notes
* Without using String.contains(), String.indexOf()
* Using String.contains(), String.indexOf()

## Solution - Without using String.contains(), String.indexOf()
```java
class Solution {
    public int numUniqueEmails(String[] emails) {
        Set<String> set = new HashSet<>();
        StringBuilder sb = new StringBuilder();
        for (String e : emails){
            for (int i = 0; i < e.length(); i++){
                if (e.charAt(i) == '.') continue;
                else if (e.charAt(i) == '+') while (e.charAt(i+1) != '@') i++;
                else if (e.charAt(i) == '@') sb.append(e.substring(i, e.length()));
                else sb.append(e.charAt(i)+"");
            }
            set.add(sb.toString());
            sb.setLength(0);
        }
        return set.size();
    }
}
```
#### Complexity
* Time Complexity: O(n*s)
* Space Complexity: O(n)

## Solution - Using String.contains(), String.indexOf()
```java
class Solution {
    public int numUniqueEmails(String[] emails) {
        Set<String> seen = new HashSet();
        for (String email: emails) {
            int i = email.indexOf('@');
            String local = email.substring(0, i);
            String rest = email.substring(i);
            if (local.contains("+")) {
                local = local.substring(0, local.indexOf('+'));
            }
            local = local.replaceAll(".", "");
            seen.add(local + rest);
        }

        return seen.size();
    }
}
```
#### Complexity
* Time Complexity: O(n)
* Space Complexity: O(n)
