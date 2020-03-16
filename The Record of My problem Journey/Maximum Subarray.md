# Maximum Subarray

Citation: https://leetcode.com/problems/maximum-subarray/


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




### Knowledges(notes)

+ Arrays.copyOfRange(nums[] , from , to)   &nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;  to obtain the sum of contiguous element. 

+ The Google Coding Standards


## The second solution (Divide and Conquer approach)

### Strategy 

Traversing the array gets the sum of some elements that is biggest.


### Code
```java
class Solution {
    
  public int crossSum(int[] nums, int left, int right, int p) {
      
    if (left == right) return nums[left];// if the left is equal with the right, it expresses there is only one element in Array.
    
    //left
    int currSum = 0;
    int leftSubsum = Integer.MIN_VALUE;
    
      
    for(int i = p; i > left - 1; --i) {//from the middle to the left
        
      currSum += nums[i];
      leftSubsum = Math.max(leftSubsum, currSum);
        
    }

    //right 
    currSum = 0;
    int rightSubsum = Integer.MIN_VALUE;
    
      
    for(int i = p + 1; i < right + 1; ++i) {//from the middle to the right
        
      currSum += nums[i];
      rightSubsum = Math.max(rightSubsum, currSum);
        
    }

    return leftSubsum + rightSubsum;//return sum of all elements
      
  }

    
  public int helper(int[] nums, int left, int right) {
    
    
    if (left == right) return nums[left];// if the left is equal with the right, it expresses there is only one element in Array.
    
    int p = (left + right) / 2; //This line of program to give a certain middle number that is integer.

    int leftSum = helper(nums, left, p);
    int rightSum = helper(nums, p + 1, right);
    int crossSum = crossSum(nums, left, right, p);

    return Math.max(Math.max(leftSum, rightSum), crossSum);//return the largest number
      
  }

    
  public int maxSubArray(int[] nums) {
      
    return helper(nums, 0, nums.length - 1);    //calling the function of helper
  
  }
}
```



### Analysis

#### Complexity

+ Time Complexity: O(n<sup>3</sup>)

+ Space Complexity: O(1)

#### Drawbacks

+ The speed of algorithm is too slow.




### Knowledges(notes)

+ Arrays.copyOfRange(nums[] , from , to)   &nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp; &nbsp;&nbsp;&nbsp;&nbsp;  to obtain the sum of contiguous element. 

+ The Google Coding Standards





