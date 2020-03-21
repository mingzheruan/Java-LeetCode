# [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)


## Description of Problem

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.



``` 
Example:

Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.

```


## The first solution (Brute Force)

### Strategy 

Traversing the array gets the sum of some elements that is biggest.


### Code

```java
class Solution {
    public int maxSubArray(int[] nums) {
        
        int largestSum = nums[0];
        
        
            for(int q=0;q<nums.length;q++){

                for(int i=0;i<nums.length && i+q<nums.length;i++){

                    int comparisonSum = 0;
                    int subarray[] = Arrays.copyOfRange(nums,i,i+q+1);

                    for(int j=0;j<subarray.length;j++){

                        comparisonSum = comparisonSum + subarray[j];

                    }

                    if(comparisonSum > largestSum){

                        largestSum = comparisonSum;

                    }else{}
                }
            }
        
        return largestSum;
        
    }
}
```



### Analysis

#### Complexity

+ Time Complexity: O(n<sup>3</sup>)

+ Space Complexity: O(1)

#### Drawbacks

+ The speed of algorithm is too slow.




### Knowledges

+ Arrays.copyOfRange(nums[] , from , to)   &nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;  to obtain the sum of contiguous element. 

+ The Google Coding Standards