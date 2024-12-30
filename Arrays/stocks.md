# Array questions

#### Question 
https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

```java
// class Solution {
//     public int maxProfit(int[] prices) {
//         int min = Integer.MAX_VALUE;
//         int maxPro = 0;
//         int max=0;
//         for(int i=0;i<prices.length;i++){
//             if(min > prices[i]){
//                 min = prices[i];
//             }
//             maxPro = prices[i]-min;
//            max = Math.max(maxPro,max); 
//         }
//         return max;
//     }
// }

class Solution {
    public int maxProfit(int[] prices) {
        int min=Integer.MAX_VALUE;
        int max=0;
        for(int i=0;i<prices.length;i++){
            if(prices[i]<min)min=prices[i];
            if(prices[i]-min>max)max=prices[i]-min;
        }  
    return max;
        
    }
}	
```
