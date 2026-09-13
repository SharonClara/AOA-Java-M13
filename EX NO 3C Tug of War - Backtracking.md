# EX 3C Tug of War problem - Backtracking.
## AIM:
To write a Java program to for given constraints.
Given an integer array nums, return true if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or false otherwise.
Example 1:
Input: Enter the number of elements: 4
Enter the elements of the array:
1 5 11 5
Output: true
Explanation: The array can be partitioned as [1, 5, 5] and [11].

Constraints:

1 <= nums.length <= 200
1 <= nums[i] <= 100

## Algorithm
1.Add all numbers in the array.

2.If the total is odd, return false (cannot split equally).

3.Set target = total / 2.

4.Use a boolean array dp to track which sums are possible.

5.For each number, update dp to mark new reachable sums.

6.If dp[target] is true, return true; otherwise return false.

## Program:

Program to implement Reverse a String
## Developed by: SHARON CLARA A
## Register Number: 212224040310 


```
import java.util.*;

public class Solution {

    public boolean canPartition(int[] nums) {
        int total = 0;
        for (int num : nums)
            total += num;

        if (total % 2 != 0)
            return false;

        int target = total / 2;
        boolean[] dp = new boolean[target + 1];
        dp[0] = true;

        for (int num : nums) {
            for (int j = target; j >= num; j--) {
                dp[j] = dp[j] || dp[j - num];
            }
        }

        return dp[target];
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }
        Solution sol = new Solution();
        boolean result = sol.canPartition(nums);
        System.out.println(result);
        sc.close();
    }
}



```

## Output:

<img width="415" height="249" alt="650878253-f90b4f6d-b4c2-43aa-b78a-7f110b21d3ff" src="https://github.com/user-attachments/assets/47c01811-17d4-41d0-8ecb-7f3411e8c861" />



## Result:
The program successfully implemented and the expected output is verified.
