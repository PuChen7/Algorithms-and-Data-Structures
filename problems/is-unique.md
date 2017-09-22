# Is Unique - Arrays and Strings
## Implement an algorithm to determine if a string has all unique characters.

```java
    public boolean isUnique(String str){
        // can't have a string of unique chars beyond 128 chars.
        if (str.length() > 128){
            return false;
        }

        // using ASCII value to check each char in boolean array.
        // if find a false, return directly
        boolean[] arr = new boolean[128];
        for (int i = 0; i < str.length(); i++){
            int ascii = (int)str.charAt(i);
            if (arr[ascii] == true){
                return false;
            }
            arr[ascii] = true;
        }
        return true;
    }
```

## Time Complexity:

O(n). n is the length of the string. The program only goes through the string once.

## Another Solution:
If we can modify the string, then we can sort the string first and find the duplicate.
Sorting time complexity will be O(nlogn). But it might take more space.