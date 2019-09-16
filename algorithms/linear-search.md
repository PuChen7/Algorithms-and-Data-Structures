# Linear Search

Given an array arr[] of n elements, write a function to search a given element x in arr[].
```java
public static int search(int arr[], int x) 
{ 
    int n = arr.length; 
    for(int i = 0; i < n; i++) 
    { 
        if(arr[i] == x) 
            return i; 
    } 
    return -1; 
} 
```

# Complexity: O(n)
