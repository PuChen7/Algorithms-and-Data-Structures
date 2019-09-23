# Get all subsequence of a String

```java
public static Set<String> getSubseqs(String s) {
    Set<String> res = new HashSet<>();
    if (s.length() == 0) {
         res.add("");
         return res;
    }
    Set<String> subRes = getSubseqs(s.substring(1));
    res.addAll(subRes);
    for (String seq : subRes) res.add(s.charAt(0) + seq);
    return res;
}
```
