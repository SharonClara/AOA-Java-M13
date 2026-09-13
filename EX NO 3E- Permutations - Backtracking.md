# EX 3E Generate Permutations using Backtracking  Approach.
## AIM:
To write a Java program to for given constraints.
Given an array nums of distinct integers, return all the possible Permutation. You can return the answer in any order.
Example 1:
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
For example:
## Algorithm
1.Start with an empty list curr that will hold the current permutation.

2.If curr contains all numbers (size equals input length), add a copy of curr to the final answer list.

3.Otherwise, loop through each number in the input array.

4.Skip a number if it is already present in curr.

5.Add the number to curr, then recursively build the remaining part of the permutation.

6.After recursion returns, remove the last number from curr (backtracking), and continue with the next choice

## Program:

Program to implement Reverse a String
## Developed by: SHARON CLARA A
## Register Number: 212224040310 
```

import java.util.*;

public class Solution {

    public List<List<Integer>> permute(int[] nums) {
        List<List<Integer>> ans = new ArrayList<>();
        backtrack(new ArrayList<>(), ans, nums);
        return ans;
    }

    public void backtrack(List<Integer> curr, List<List<Integer>> ans, int[] nums) {
        if (curr.size() == nums.length) {
            ans.add(new ArrayList<>(curr));
            return;
        }

        for (int num : nums) {
            if (curr.contains(num)) continue;
            curr.add(num);
            backtrack(curr, ans, nums);  
            curr.remove(curr.size() - 1); 
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String inputLine = scanner.nextLine().trim();
        inputLine = inputLine.replaceAll(".*\\[|\\].*", "");
        String[] parts = inputLine.split(",");

        int[] nums = new int[parts.length];
        for (int i = 0; i < parts.length; i++) {
            nums[i] = Integer.parseInt(parts[i].trim());
        }

        Solution solution = new Solution();
        List<List<Integer>> permutations = solution.permute(nums);
        System.out.println(permutations);
        scanner.close();
    }
}

```
## Output:

<img width="913" height="241" alt="650879706-3ac06af7-30ab-4ae8-8eb9-887ec910b15b" src="https://github.com/user-attachments/assets/c41a9087-1d4a-40ad-9c34-ecac33c389b1" />



## Result:
The program successfully implemented and the expected output is verified.
