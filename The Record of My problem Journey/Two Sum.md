# Two Sum

Citation: https://leetcode.com/problems/two-sum/  


## Description of Problem

Given an array of integers, return indices of the two numbers such that they add up to a specific target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.


``` 
Example:

Given nums = [2, 7, 11, 15], target = 9,
Because nums[0] + nums[1] = 2 + 7 = 9,
return [0, 1].
```


## The first time

### Strategy 

Traversing the array to find the sum of two different elements equals the target.


### Code
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
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


### Details

Runtime: 106 ms, faster than 5.12% of Java online submissions for Two Sum.

Memory Usage: 39.7 MB, less than 5.65% of Java online submissions for Two Sum.

### Complexity Analysis

+ Time Complexity: O(n<sup>2</sup>)

+ Space Complexity: O(1)

### Drawbacks

## The second time



