# Bubble Sort
Bubble Sort is the simplest sorting algorithm that works by repeatedly swapping the adjacent elements if they are in wrong order.

```java
public class playground{
    public static void main(String args[]){
        int[] nums = {4,3,2,1,5};

        for (int i = 0; i < nums.length-1; i++){
            for (int j = 0; j < nums.length-i-1; j++){
                if (nums[j]>nums[j+1]){
                    int tmp = nums[j];
                    nums[j] = nums[j+1];
                    nums[j+1] = tmp;
                }
                System.out.println("\n");
            }
        }
    }
}
```

## Complexity
O(n^2)