# Array questions
Array Leaders


#### Question 1
https://www.geeksforgeeks.org/problems/leaders-in-an-array-1587115620/0

```java
class Solution {
    static ArrayList<Integer> leaders(int arr[]) {
        // code here
        ArrayList<Integer> list = new ArrayList<>();
        int max = Integer.MIN_VALUE;
        int n= arr.length;
        
        for(int i=n-1;i>=0;i--){
            if(arr[i]>=max){
                list.add(arr[i]);
                max = arr[i];
            }
        }
        Collections.reverse(list);
        return list;
    }
}
	
```
