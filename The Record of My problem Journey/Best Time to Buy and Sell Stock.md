# Best Time to Buy and Sell Stock

Citation of Problem: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/


## Description of Problem

Say you have an array for which the *i*th element is the price of a given stock on day *i*.

If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.

Note that you cannot sell a stock before you buy one.



``` 
Example 1:

Input: [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
             Not 7-1 = 6, as selling price needs to be larger than buying price.


Example 2:

Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.

```


## The first solution (Brute Force)

### Strategy 

Traversing the array gets the sum of some elements that is biggest.


### Code

```java
class Solution {
    
    /*basicSum
    
    Function: Solving the basci problems
    
    */
    
    public int basicSum(int [] prices, int left, int right , int p){
        
        int biggestValue = Integer.MIN_VALUE;
        int corrsum = 0;
        
        
        for(int i = right; i > left - 1 ; --i){
            for(int j = i ; j > left -1 ; --j){
                
                corrsum = prices[i] - prices[j];
                biggestValue = Math.max(corrsum, biggestValue);
                
            }
        }
        
        if(biggestValue < 0){
            return 0;
        }else{
            return biggestValue;
        }
        
    }
    
    
    /*partition
    
    Function: Dividing a big problem into some same and basic problems 
              decreases the computation in order to simplify the question.
    
    */
    
    public int partition(int [] prices, int left , int right){
        
        if(left == right) return 0;
        
        int p = (left + right)/2;
        
        int leftSum = partition(prices, left , p);
        int rightSum = partition(prices, p + 1 , right);
        int corrSum = basicSum(prices, left , right , p);
        
        return Math.max(Math.max(leftSum,rightSum),corrSum);
        
    }
    
    
    
    public int maxProfit(int[] prices) {
        
        return partition(prices, 0 , prices.length - 1);
        
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





## The Second solution (one pass)

### Strategy 

We can compute the spread between the biggest price and the smallest price.


### Code

```java
class Solution {
    public int maxProfit(int[] prices) {
        
        int maxprofit = 0;
        int minprice = Integer.MAX_VALUE;
        
        for(int i = 0; i < prices.length ; i++){
            
            if(prices[i] < minprice){
                
                minprice = prices[i];
                
            }else if(prices[i] - minprice > maxprofit){
                
                maxprofit = prices[i] - minprice;
                
            }
            
        }
        
        return maxprofit;
        
    }
    
}
```



### Analysis

#### Complexity

+ Time Complexity: O(n)

+ Space Complexity: O(1)




### Knowledges

+ We should analysis the meaning of problems carefully.

  
