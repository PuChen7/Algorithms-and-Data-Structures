# Insertion Sort

```java
import java.util.Arrays;

public class playground{
    public static void main(String args[]){
        int[] nums = {4,2,11,1,5};

        int len = nums.length;
        for (int i = 1; i < len; i++){
            int j = i - 1;
            int key = nums[i];
            while (j >= 0 && key < nums[j]){
                nums[j+1] = nums[j];
                j = j - 1;
            }
            nums[j+1] = key;
        }
    }
}

```

## Complexity
O(n^2)

## Boundary Cases
Insertion sort takes maximum time to sort if elements are sorted in reverse order. And it takes minimum time (Order of n) when elements are already sorted.