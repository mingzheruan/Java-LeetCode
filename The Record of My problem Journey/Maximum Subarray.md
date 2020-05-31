# Maximum Subarray

Citation of Problem: https://leetcode.com/problems/maximum-subarray/


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


## The second solution (Divide and Conquer approach)

### Strategy 

Using Divide and Conquer Approach simplify the problem. Dividing the prblem into many same and small problems.




### Code
```java
class Solution {
    
    /* corrSum
    
    Function: Dividing the acquired array into two parts obtains the separately biggest value of two parts. 
    
    Signifiance: Solving the same and basis problems, which is made by the function of partition.
    
    */
    
    public int corrSum(int [] nums, int left, int right, int p){   
        
        if(left == right){  //return the single element.
            
            return nums[left];
            
        } 

        int leftSubSum = Integer.MIN_VALUE;
        int corrsum = 0;
        
        for(int i = p; i > left - 1 ; --i){
            
            corrsum += nums[i];
            leftSubSum = Math.max(leftSubSum, corrsum);
            
        }
        
        int rightSubSum = Integer.MIN_VALUE;
        corrsum = 0;
        
        for(int i = p + 1 ; i < right + 1 ; ++i){
            
            corrsum += nums[i];
            rightSubSum = Math.max(rightSubSum, corrsum);
        }
        
        return leftSubSum + rightSubSum;
        
    }
    
    
    /* partition
    
    Function: Dividing a big array into lots of parts decreases the number of calculation in order to simplify problems. 
    
    Signifiance: Dividing a big problem into many same and basis problems.
    
    */
    
    
    public int partition(int [] nums, int left, int right){
        
        if(left == right){
            
            return nums[left];
            
        }
        
        
        int p = (left + right) / 2;
        
        int leftSum = partition(nums, left , p);  
        int rightSum = partition(nums, p + 1 , right);    
        int corrsum = corrSum(nums, left , right, p);   
        
        return Math.max(Math.max(leftSum,rightSum), corrsum);   //return the biggest value
        
    }
    
    
    
    
    public int maxSubArray(int[] nums) {
        
         return partition(nums, 0 , nums.length - 1);
    
    }
}


```



### Analysis

#### Complexity

+ Time Complexity: O(N·log(N))
+ Space Complexity: O(log(N))




### Knowledges

+ how to compute the time complexity.







