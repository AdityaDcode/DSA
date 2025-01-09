# Array questions
54. Spiral Matrix


#### Question 54
https://leetcode.com/problems/spiral-matrix/description/
```java
class One{
    public List<Integer> spiralOrder(int[][] matrix) {
        List<Integer> ls = new ArrayList<>();
        int n = matrix.length;
        int m = matrix[0].length;
        int left=0;
        int top = 0;
        int right = m-1;
        int bottom = n-1;
     while(left<=right && top<=bottom){
        for(int i=left;i<=right;i++){
            ls.add(matrix[top][i]);
        }
        top++;
        for(int j=top;j<=bottom;j++){
            ls.add(matrix[j][right]);
        }
        right--;
        if(top<=bottom){
        for(int k=right; k>=left;k--){
           ls.add(matrix[bottom][k]); 
        }
        }
         bottom--;
        if(left<=right){
        for(int l= bottom;l>=top;l--){
            ls.add(matrix[l][left]);
        }
        }
        left++;
      }
      return ls;
    
}
}	
```
