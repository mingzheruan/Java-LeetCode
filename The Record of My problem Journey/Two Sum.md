# Two Sum

Citation: https://leetcode.com/problems/two-sum/  
&nbsp;

## Description of Problem

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.



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
