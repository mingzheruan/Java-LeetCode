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


## The first time (Brute Force)

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

+ Arrays.copyOfRange(nums[] , from , to)   &nbsp;   to obtain the sum of contiguous element. 




## The second time (two-pass HashMap)

### Strategy 

Using HashMap stores data and increases the efficiency of searching

### Code

``` java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();

        for(int i=0;i<nums.length;i++){
            map.put(nums[i],i);
        }

        for(int j=0;j<nums.length;j++){
            int complement = target - nums[j];
            if(map.containsKey(complement) && map.get(complement) != j){
                return new int[] {j,map.get(complement)};
            }
        }
        
        throw new IllegalArgumentException("No two sum solution");

    }
}
```

#### Details

+ Runtime: 2 ms, faster than 80.73% of Java online submissions for Two Sum.

+ Memory Usage: 41.9 MB, less than 5.65% of Java online submissions for Two Sum.

#### Complexity

+ Time Complexity: O(n)

+ Space Complexity: O(n)

#### Drawbacks

#### Attention

+ We should judge the complement whether is stored in HashMap!!!

### Cause - why cannot I get the this idea? 

I forget the knowledge of HashMap.



## The third time (one-pass HashMap)

### Strategy 

Using HashMap stores data and increases the efficiency of searching

### Code

``` java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();


        for(int j=0;j<nums.length;j++){
            int complement = target - nums[j];
            if(map.containsKey(complement) && map.get(complement) != j){
                return new int[] {j,map.get(complement)};
            }
            map.put(nums[j],j);
        }
        
        throw new IllegalArgumentException("No two sum solution");

    }
}
```

###  Analysis - why the speed of one-pass HashMap is more faster than the speed of two-pass HashMap? what's advantage?

+ Decreasing the number of iteration from two to one.

+ The speed of algorithm doubles its original one.


#### Details

+Runtime: 1 ms, faster than 99.89% of Java online submissions for Two Sum.

+Memory Usage: 42.3 MB, less than 5.65% of Java online submissions for Two Sum.

#### Complexity

+ Time Complexity: O(n)

+ Space Complexity: O(n)

### Cause - why cannot I get the this idea? 

I forget the knowledge of HashMap.

