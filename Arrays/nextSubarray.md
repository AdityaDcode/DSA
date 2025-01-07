# Array questions
31. Next Permutation


#### Question 1
https://leetcode.com/problems/next-permutation/description/

```java
class Solution {
    public void nextPermutation(int[] nums) {
        int n = nums.length;
        int ind =-1;
        for(int i=n-2;i>=0;i--){
            if(nums[i]<nums[i+1]){
                ind = i;
                break;
            }
        }
        if(ind == -1){
            reverse(0,n-1,nums);
            return;
        }
        for(int i= n-1;i>ind;i--){
            if(nums[i] > nums[ind]){
                int temp = nums[i];
                nums[i] = nums[ind];
                nums[ind]=temp;
                break;
            }
        }
        reverse(ind+1,n-1,nums);
    }
    public static void reverse(int s,int e,int[] arr){
        while(s<=e){
            int temp =arr[s];
            arr[s] = arr[e];
            arr[e] = temp;
            s++;
            e--;
        }
    }
}
```
