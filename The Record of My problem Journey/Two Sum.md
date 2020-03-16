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


## The first solution (Brute Force)

### Strategy 

Traversing the array gets the sum of two different elements, which equals the target.


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



### Analysis


#### Details

+ Runtime: 106 ms, faster than 5.12% of Java online submissions for Two Sum.

+ Memory Usage: 39.7 MB, less than 5.65% of Java online submissions for Two Sum.

#### Complexity

+ Time Complexity: O(n<sup>2</sup>)

+ Space Complexity: O(1)

#### Drawbacks

+ The speed of algorithm is slow.

### Cause - why cannot I get the better idea? 

I forget the knowledge.

I need to practice more algorithm.






## The second solution (two-pass HashMap)

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



## The third solution (one-pass HashMap)

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
