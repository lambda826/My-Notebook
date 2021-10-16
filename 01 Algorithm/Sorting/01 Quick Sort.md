# Quick Sort
## Overview
> Process (Divide-and-Conquer paradigm):
>    - Pick an element as pivot X.
>    - Partition the given array into two subarrays around the pivot X.
>    - Put X at its correct position in sorted array and put all smaller elements (smaller than X) before X, and put all greater elements (greater than X) after X.
>    - Recursively quicksort the two subarrays.
> ---
> Performance
> - **Unstable**
> - Time Complexity
>   - Average: **O(n log n)**
>   - Best case: O(n)
>   - Worst case: O(n^2^)
>  - Space Complexity
>    - O(1)
> ---
> Note
> - There are many different versions of quickSort that pick pivot in different ways:
>   - Always pick first element as pivot.
>   - Always pick last element as pivot.
>   - Pick a random element as pivot.
>   - Pick median as pivot.

## Implementation

```java
    private void quickSort(int[] nums, int left, int right) {
        if (left < right) {
            int indexPivot = partition(nums, left, right);
            // int indexPivot = partition2(nums, left, right);
            quickSort(nums, left, indexPivot - 1);
            quickSort(nums, indexPivot + 1, right);
        }
    }
    
    private int partition(int[] nums, int left, int right) {
        int idx = right;
        swap(nums, ThreadLocalRandom.current().nextInt(left, right + 1), right);
        while (left < right) {
            while (left < right && nums[left] < nums[idx]) {
                left++;
            }
            while (left < right && nums[right] >= nums[idx]) {
                right--;
            }
            swap(nums, left, right);
        }
        swap(nums, left, idx);
        return left;
    }


    private void swap(int[] nums, int i, int j) {
        int temp = nums[i];
        nums[i] = nums[j];
        nums[j] = temp;
    }
```
---
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcyNzA5ODcxNl19
-->