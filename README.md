# Java-Leetcode
Coding for familiarizing algorithm 


```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
       Map m1 = new HashMap();
            for(int i=0;i<=nums.length;i++){
                for(int j=0; j<nums.length;j++){
                     if(nums[j] + nums[i+1] == target){
                         if(i+1 != j){
                              return new int[] {j,i+1};
                         }
                     }   
                } 
             }
        throw new IllegalArgumentException("No solution of two sum");
    }
}
```
