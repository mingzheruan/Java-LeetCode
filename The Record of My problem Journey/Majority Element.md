# Maximum Element

Citation of Problem: https://leetcode.com/problems/majority-element/


## Description of Problem

Given an array of size *n*, find the majority element. The majority element is the element that appears **more than** `⌊ n/2 ⌋` times.

You may assume that the array is non-empty and the majority element always exist in the array.



``` 
Example1:

Input: [3,2,3]
Output: 3



Example 2:

Input: [2,2,1,1,1,2,2]
Output: 2
```



## The first solution (Divide and Conquer approach)

### Strategy 

Using Divide and Conquer Approach simplify the problem. Dividing the prblem into many same and small problems.




### Code

```java
class Solution {
    
    private int countMode(int [] nums, int target){
        
        int count = 0;
        
        for(int i = 0; i<=nums.length-1; i++){
            if(nums[i] == target){
                count++;
            }
        }
        
        return count;
    }
    
    
    private int partition(int [] nums, int left, int right){
        
        if(left == right){
            
            return nums[left];
            
        }
        
        int mid = (left + right)/2;
        
        int leftMode = partition(nums, left, mid);
        int rightMode = partition(nums, mid+1, right);
        
        if(leftMode == rightMode){
            
            return leftMode;
            
        }
        
        int countLeftMode = countMode(nums,leftMode);
        int countRightMode = countMode(nums,rightMode);
            
            
        return countLeftMode > countRightMode ? leftMode : rightMode;
    }
    
    
    public int majorityElement(int[] nums) {
        
        return partition(nums, 0, nums.length - 1) ;
            
    }
}
```



### Analysis

#### Complexity

+ Time Complexity: O(N·log(N))
+ Space Complexity: O(log(N))




### Knowledges

+ how to compute the time complexity.







