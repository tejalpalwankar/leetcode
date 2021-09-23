# 509. Fibonacci Number
Easy

The Fibonacci numbers, commonly denoted F(n) form a sequence, called the Fibonacci sequence, such that each number is the sum of the two preceding ones, starting from 0 and 1. That is,

F(0) = 0, F(1) = 1
F(n) = F(n - 1) + F(n - 2), for n > 1.
Given n, calculate F(n).
<pre>
Example 1:

Input: n = 2
Output: 1
Explanation: F(2) = F(1) + F(0) = 1 + 0 = 1.
Example 2:

Input: n = 3
Output: 2
Explanation: F(3) = F(2) + F(1) = 1 + 1 = 2.
Example 3:

Input: n = 4
Output: 3
Explanation: F(4) = F(3) + F(2) = 2 + 1 = 3.
</pre>

```C++ 
int fib(int n) {
    int output[31];
    
    output[0] = 0;
    output[1] = 1;
    output[2] = 1;
    
    for(int i =3 ; i <= n ; i++){
        output[i] = output[i-1] + output[i-2];
    }
    
    return output[n];

}
```

# 1137. N-th Tribonacci Number
Easy

The Tribonacci sequence Tn is defined as follows: 

T0 = 0, T1 = 1, T2 = 1, and Tn+3 = Tn + Tn+1 + Tn+2 for n >= 0.

Given n, return the value of Tn.

<pre>
Example 1:

Input: n = 4
Output: 4
Explanation:
T_3 = 0 + 1 + 1 = 2
T_4 = 1 + 1 + 2 = 4
Example 2:

Input: n = 25
Output: 1389537
</pre>
```C++ 
int tribonacci(int n) {
    int output[38];
    
    output[0] = 0;
    output[1] = 1;
    output[2] = 1;
    
    for(int i =3 ; i <= n ; i++){
        output[i] = output[i-1] + output[i-2] + output[i-3];
    }
    
    return output[n];
}
```
# 70. Climbing Stairs
Easy

You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

<pre>
Example 1:

Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
Example 2:

Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
</pre>

```C++ 
    int climbStairs(int n) {
        int output[46];
        
        output[0] = 0;
        output[1] = 1;
        output[2] = 2;
        
        for(int i = 3 ; i <=n ; i++){
            output[i] = output[i-1] + output[i-2] ;
        }
        return output[n];
        
    }
```

# 746. Min Cost Climbing Stairs
Easy

You are given an integer array cost where cost[i] is the cost of ith step on a staircase. Once you pay the cost, you can either climb one or two steps.

You can either start from the step with index 0, or the step with index 1.

Return the minimum cost to reach the top of the floor.
<pre>
Example 1:

Input: cost = [10,15,20]
Output: 15
Explanation: Cheapest is: start on cost[1], pay that cost, and go to the top.
Example 2:

Input: cost = [1,100,1,1,1,100,1,1,100,1]
Output: 6
Explanation: Cheapest is: start on cost[0], and only step on 1s, skipping cost[3].
</pre>

```C++ 
int minCostClimbingStairs(vector<int>& cost) {
    int n = cost.size();
    int output[n];
    
    output[0] = cost[0];
    output[1] = cost[1];
    
    
    for(int i= 2 ; i < n ; i++){
        output[i] = cost[i] + min(output[i-1], output[i-2]);
    }
    
    return min(output[n-1], output[n-2]);
}
```
# 198. House Robber
Medium

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.

<pre>
Example 1:

Input: nums = [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.
Example 2:

Input: nums = [2,7,9,3,1]
Output: 12
Explanation: Rob house 1 (money = 2), rob house 3 (money = 9) and rob house 5 (money = 1).
Total amount you can rob = 2 + 9 + 1 = 12.
</pre>

```C++ 
int rob(vector<int>& nums) {
    if (nums.size() == 0) 
    {return 0;}
    if (nums.size() == 1) 
    {return nums[0];}
    int n = nums.size();
    int *output = new int[n+1];
    
    output[0] = nums[0];
    output[1] = max(nums[1], nums[0]);

    
    for(int i =2 ; i < n ; i++){
        output[i] = max(output[i-2] + nums.at(i), output[i-1]);
    }
    

    return output[n-1];
    }
```
# 213. House Robber II
Medium

You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are arranged in a circle. That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have a security system connected, and it will automatically contact the police if two adjacent houses were broken into on the same night.

Given an integer array nums representing the amount of money of each house, return the maximum amount of money you can rob tonight without alerting the police.
<pre>
Example 1:

Input: nums = [2,3,2]
Output: 3
Explanation: You cannot rob house 1 (money = 2) and then rob house 3 (money = 2), because they are adjacent houses.
Example 2:

Input: nums = [1,2,3,1]
Output: 4
Explanation: Rob house 1 (money = 1) and then rob house 3 (money = 3).
Total amount you can rob = 1 + 3 = 4.
Example 3:

Input: nums = [1,2,3]
Output: 3
</pre>

```C++ 
    int rob(vector<int>& nums) {
        if (nums.size() == 0) 
        {return 0;}
        if (nums.size() == 1) 
        {return nums[0];}
        int n = nums.size();
        int *output1 = new int[n+1];
        int *output2 = new int[n+1];

        output1[0] = nums[0];
        output1[1] = max(nums[1], nums[0]);

        
        for(int i =2 ; i < n ; i++){
            output1[i] = max(output1[i-2] + nums.at(i), output1[i-1]);
        }
        output1[n-1] = 0;

        
        output2[0] = 0;
        output2[1] = nums[1];

        
        for(int i =2 ; i < n ; i++){
            output2[i] = max(output2[i-2] + nums.at(i), output2[i-1]);
        }
        return max(output1[n-2], output2[n-1]);
        // return output1[n-2];
    }
```
# 55. Jump Game
medium

You are given an integer array nums. You are initially positioned at the array's first index, and each element in the array represents your maximum jump length at that position.

Return true if you can reach the last index, or false otherwise.

<pre>
Example 1:

Input: nums = [2,3,1,1,4]
Output: true
Explanation: Jump 1 step from index 0 to 1, then 3 steps to the last index.
Example 2:

Input: nums = [3,2,1,0,4]
Output: false
Explanation: You will always arrive at index 3 no matter what. Its maximum jump length is 0, which makes it impossible to reach the last index.
</pre>

```C++ 
    bool helper(vector<int>& nums , int n){
        int reach =0;
        int i;
        for(i = 0 ; i < n && i <= reach; i++){
            reach = max(i + nums[i] , reach);
        }
        
        return n == i;
    }
    
    bool canJump(vector<int>& nums) {
        int n = nums.size();
        return helper(nums , n);
    }
```

# 53. Maximum Subarray
Easy 

Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

A subarray is a contiguous part of an array.

## Appraoch 
<pre>
Kadane’s Algorithm:

Initialize:
    max_so_far = INT_MIN
    max_ending_here = 0

Loop for each element of the array
  (a) max_ending_here = max_ending_here + a[i]
  (b) if(max_so_far < max_ending_here)
            max_so_far = max_ending_here
  (c) if(max_ending_here < 0)
            max_ending_here = 0
return max_so_far
</pre>
The simple idea of Kadane’s algorithm is to look for all positive contiguous segments of the array (max_ending_here is used for this). And keep track of maximum sum contiguous segment among all positive segments (max_so_far is used for this). Each time we get a positive-sum compare it with max_so_far and update max_so_far if it is greater than max_so_far 

```C++ 
    int maxSubArray(vector<int>& nums) {
        int n = nums.size();
        int *output = new int[n];
        int maxSoFar= nums[0] , maxEndHere = 0;
        for(int i =0 ; i < n; i++){
            maxEndHere += nums[i];
            if(maxSoFar < maxEndHere){
                maxSoFar = maxEndHere;
            }
            if(maxEndHere <= 0){
                maxEndHere = 0;
            }
        }
         
        return maxSoFar;
    }
```

# 918. Maximum Sum Circular Subarray
Medium

Given a circular integer array nums of length n, return the maximum possible sum of a non-empty subarray of nums.

A circular array means the end of the array connects to the beginning of the array. Formally, the next element of nums[i] is nums[(i + 1) % n] and the previous element of nums[i] is nums[(i - 1 + n) % n].

A subarray may only include each element of the fixed buffer nums at most once. Formally, for a subarray nums[i], nums[i + 1], ..., nums[j], there does not exist i <= k1, k2 <= j with k1 % n == k2 % n.

### Approach
The maximum subarray sum in circular array is maximum of following

Maximum subarray sum in non circular array
Maximum subarray sum in circular array.
Example - [1,2,5,-2,-3,5]
Steps -

Find the maximum subarray sum using Kadane Algorithm. This is maximum sum for non circular array.
image
1+2+5 = 8
For non circular sum,
Step 1) find the minimum subarray sum of array.
image
-2-3 =-5
Step 2) Now find the total sum of array = 1 + 2 + 5 -2 - 3 + 5 = 8
Step 3) The max subarray sum for circular array = Total Sum - Minimum subarray Sum
= 8 - (-5) = 8 + 5 =13
image
As illustrated above, substracting minimum subarray sum from total sum gives maximum circular subarray sum.
Answer = Max ( Non circular max sum + circular max sum )= max(8,13) = 13
Code -
The trick here is that to find the minimum subarray sum, we invert the sign of all the numbers in original subarray, and find the maximum subarray sum using Kadane algorithm. Then add it with the total sum. (which is similar to

```C++ 
int maxSubarraySumCircular(vector<int>& nums) {
        int n = nums.size();

        int maxSoFar= nums[0] , maxEndHere = 0;
        for(int i =0 ; i < n; i++){
            maxEndHere += nums[i];
            if(maxSoFar < maxEndHere){
                maxSoFar = maxEndHere;
            }
            if(maxEndHere <= 0){
                maxEndHere = 0;
            }
        }
        
        int minSoFar = nums[0] , minEndHere =0, total = 0;
        for(int i =0 ; i < n ; i++){
            minEndHere += nums[i];
            total += nums[i];
            if(minSoFar > minEndHere){
                minSoFar = minEndHere;
            }
            if(minEndHere > 0){
                minEndHere = 0;
            }
        }
        
        int ans = max(maxSoFar , total - minSoFar);
        
        
        return maxSoFar > 0 ? ans : maxSoFar;

    }
```

### Output 
<pre>
input : 
[1,-2,3,-2]
[5,-3,5]
[3,-1,2,-1]
[3,-2,2,-3]
[-2,-3,-1]
[1,-6,-7,4]

output: 
3
10
4
3
-1
5

</pre>