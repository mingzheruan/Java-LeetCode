# Best Time to Buy and Sell Stock II

Citation of Problem: https://leetcode.com/problems/best-time-to-buy-and-sell-stock/


## Description of Problem

Say you have an array `prices` for which the *i*th element is the price of a given stock on day *i*.

Design an algorithm to find the maximum profit. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).

**Note:** You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).



``` 
Example 1:

Input: [7,1,5,3,6,4]
Output: 7
Explanation: Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
             Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.

Example 2:

Input: [1,2,3,4,5]
Output: 4
Explanation: Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
             Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are
             engaging multiple transactions at the same time. You must sell before buying 	    						 again.
             
             
Example 3:

Input: [7,6,4,3,1]
Output: 0
Explanation: In this case, no transaction is done, i.e. max profit = 0.



Constraints:
  1 <= prices.length <= 3 * 10 ^ 4
  0 <= prices[i] <= 10 ^ 4
```


## The first solution (Brute Force)

### Strategy 

Traversing the array gets the sum of some elements that is biggest.


### Code

```java
class Solution {
    public int maxProfit(int[] prices) {
        
        int maxprofit =  0;
        int minprice = Integer.MAX_VALUE;
        int profits[][] = new int[prices.length][prices.length];
        
        for(int i = 0; i<prices.length; i++){
            for(int j = 0; j<prices.length; j++){
                
                if(j <= i){
                    
                    profits[i][j] = 0;
                
                }else if{
                    
                    profits[i][j] = prices[i] - prices[j];
                
                    }
                }
            }
        
        for(int i = 0; i<prices.length; i++){
            for(int j = 0; j<prices.length; j++){
            
            if(maxprofit < profits[i][j]){
                
            }
            
                
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

