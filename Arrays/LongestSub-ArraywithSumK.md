# Longest Subarray with Sum Equal to K

## Problem Statement
Given an array of integers and a target sum \( k \), find the length of the longest subarray that sums to \( k \). If no such subarray exists, return 0.

---

## Approach
We use the **two-pointer technique** (sliding window) to solve this problem efficiently in \( O(n) \) time complexity. Below are the steps involved:

### Steps
1. **Initialize Two Pointers**:
   - `left` points to the start of the current subarray.
   - `right` points to the end of the current subarray.

2. **Maintain a Running Sum**:
   - Use a variable `sum` to keep track of the sum of elements in the current subarray.

3. **Adjust the Window**:
   - If `sum > k`, shrink the window by incrementing `left` and subtracting the element at `left` from `sum`.
   - If `sum == k`, calculate the length of the subarray (`right - left + 1`) and update `maxLen`.

4. **Expand the Window**:
   - Move the `right` pointer forward and add the new element to `sum`.

5. **Continue Until the Right Pointer Crosses the Array**.

---

## Code Implementation
```java
import java.util.*;

public class Main {
    public static int getLongestSubarray(int[] a, long k) {
        int n = a.length; // Size of the array

        int left = 0, right = 0; // Two pointers
        long sum = a[0];
        int maxLen = 0;

        while (right < n) {
            // If sum > k, reduce the subarray from the left
            while (left <= right && sum > k) {
                sum -= a[left];
                left++;
            }

            // If sum == k, update the max length
            if (sum == k) {
                maxLen = Math.max(maxLen, right - left + 1);
            }

            // Move the right pointer forward
            right++;
            if (right < n) sum += a[right];
        }

        return maxLen;
    }

    public static void main(String[] args) {
        int[] a = {2, 3, 5, 1, 9};
        long k = 10;
        int len = getLongestSubarray(a, k);
        System.out.println("The length of the longest subarray is: " + len);
    }
}
```

---

## Explanation with Example
### Input:
```
Array: [2, 3, 5, 1, 9]
K: 10
```

### Execution:
1. **Initial State**:
   ```
   left = 0, right = 0, sum = 2, maxLen = 0
   ```

2. **Step 1** (`right = 1`):
   - Add `a[right] = 3` to `sum`: `sum = 2 + 3 = 5`.
   - `sum < k`, move `right` forward.

3. **Step 2** (`right = 2`):
   - Add `a[right] = 5` to `sum`: `sum = 5 + 5 = 10`.
   - `sum == k`, update `maxLen = max(0, 2 - 0 + 1) = 3`.
   - Move `right` forward.

4. **Step 3** (`right = 3`):
   - Add `a[right] = 1` to `sum`: `sum = 10 + 1 = 11`.
   - `sum > k`, shrink the subarray:
     - Subtract `a[left] = 2`: `sum = 11 - 2 = 9`, `left = 1`.
   - Move `right` forward.

5. **Step 4** (`right = 4`):
   - Add `a[right] = 9` to `sum`: `sum = 9 + 9 = 18`.
   - `sum > k`, shrink the subarray:
     - Subtract `a[left] = 3`: `sum = 18 - 3 = 15`, `left = 2`.
     - Subtract `a[left] = 5`: `sum = 15 - 5 = 10`, `left = 3`.
   - `sum == k`, update `maxLen = max(3, 4 - 3 + 1) = 3`.

### Output:
```
The length of the longest subarray is: 3
```

---

## Complexity Analysis
### Time Complexity:
- **Outer Loop**: The `right` pointer traverses the array once: \( O(n) \).
- **Inner Loop**: The `left` pointer also traverses the array, but each element is visited at most once.
- Overall: \( O(n) \).

### Space Complexity:
- No extra space is used apart from a few variables.
- Overall: \( O(1) \).

---

## Edge Cases
1. **No Subarray Exists**:
   - Input: `a = [1, 2, 3]`, `k = 10`
   - Output: `0`

2. **All Elements Sum to K**:
   - Input: `a = [2, 3, 5]`, `k = 10`
   - Output: `3`

3. **Single Element Equals K**:
   - Input: `a = [10, 2, 3]`, `k = 10`
   - Output: `1`

---

## Intuition
We use the two-pointer approach to dynamically adjust the size of the subarray. By moving the `right` pointer forward, we explore new elements. If the sum exceeds \( k \), we shrink the subarray from the left to try and bring the sum back to \( k \). This ensures that we find the longest subarray efficiently.

