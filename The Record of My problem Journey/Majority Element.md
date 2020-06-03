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

Here, we apply a classical divide & conquer approach that recurses on the left and right halves of an array until an answer can be trivially achieved for a length-1 array. Note that because actually passing copies of subarrays costs time and space, we instead pass `lo` and `hi` indices that describe the relevant slice of the overall array. In this case, the majority element for a length-1 slice is trivially its only element, so the recursion stops there. If the current slice is longer than length-1, we must combine the answers for the slice's left and right halves. If they agree on the majority element, then the majority element for the overall slice is obviously the same[[1\]](https://leetcode.com/problems/majority-element/solution/#fn1). If they disagree, only one of them can be "right", so we need to count the occurrences of the left and right majority elements to determine which subslice's answer is globally correct. The overall answer for the array is thus the majority element between indices 0 and 


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

#### Details

+ Runtime: 1 ms, faster than 99.67% of Java online submissions for Majority Element.

+ Memory Usage: 42.8 MB, less than 42.65% of Java online submissions for Majority Element.




### Knowledges

+ 







