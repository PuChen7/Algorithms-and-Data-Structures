# Get all subsequence of a String

```java
public List<String> subString(String s) {
    List<String> sub = new ArrayList<>();
    for (int i = 0; i < s.length(); i++){
       for (int j = i+1; j <= s.length(); j++){
            sub.add(s.substring(i, j));
        } 
    }
    return sub;
} 
```
