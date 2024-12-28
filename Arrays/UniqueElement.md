# Array questions
136. Single Number


#### Question 1
https://leetcode.com/problems/single-number/description/
https://takeuforward.org/arrays/find-the-number-that-appears-once-and-the-other-numbers-twice/
```java
class Solution {
    public int singleNumber(int[] nums) {
        int result =0;
        for(int i=0;i<nums.length;i++){
            result = result^nums[i];
        }
        return result;
    }
}
```
