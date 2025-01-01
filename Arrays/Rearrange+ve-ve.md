# Array questions
2149. Rearrange Array Elements by Sign


#### Question 1
https://leetcode.com/problems/rearrange-array-elements-by-sign/description/
https://takeuforward.org/arrays/rearrange-array-elements-by-sign/

```java
class Solution {
    public int[] rearrangeArray(int[] nums) {
       int n = nums.length;
       int pos =0;
       int neg =1;
       int i=0;
       int[] arr =new int[n];
       while(i<n){
        if(nums[i]>=0 && pos<n){
            arr[pos] = nums[i];
            pos+=2;
        }else if(nums[i]<0 && neg<n){
            arr[neg] = nums[i];
            neg+=2;
        }
        i++;
       }
       return arr;
    }
}
```

