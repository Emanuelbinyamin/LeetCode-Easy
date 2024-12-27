# 🚶‍♂️ Climbing Stairs Problem Solution 🚶‍♀️

Welcome to the **Climbing Stairs** repository! This repository contains a fun and interactive solution
to the famous LeetCode problem: **Climbing Stairs**.
Here, I'll share my thought process, explain each line of code, and help you understand the magic behind finding the number of ways to climb `n` stairs. 

---

## 🎯 Problem Description
Given a staircase with `n` steps, you can climb either **1 step** or **2 steps** at a time. How many distinct ways can you climb to the top?

---

## 🧠 My Thought Process
I started solving the problem by observing how many ways I could climb small sets of stairs:

1. If there's **1 step**, there's only **1 way**: just take that single step. 
2. If there are **2 steps**, there are **2 ways**: (1 + 1) or (2).
3. For **3 steps**, I noticed a pattern! The number of ways is the **sum** of the ways to climb 1 and 2 steps.
   - Why? To reach the 3rd step, you could either:
     - Come from the 2nd step (1 way to reach step 2).
     - Or come from the 1st step (2 ways to reach step 1).

This led me to a simple recursive pattern: **`ways(n) = ways(n-1) + ways(n-2)`**.

---

## 🚀 Code Solution
The solution is implemented in C#. It uses dynamic programming to optimize the recursive solution, storing previously calculated results in an array (**`dp`**) to avoid redundant calculations.

### Solution.cs
```csharp
public class Solution {
    public int ClimbStairs(int n) {
        // Step 1: Create a dp array to store results for subproblems
        int[] dp = new int[n + 1];
        dp[1] = 1; // Base case: Only 1 way to climb 1 step

        // Step 2: Calculate and return the number of ways using helper function
        return GetWaysToClimb(n, dp);
    }

    private int GetWaysToClimb(int n, int[] dp) {
        if (n == 1) return dp[n]; // If there's 1 step, return 1

        if (n == 2) {
            dp[2] = 2; // Base case: 2 ways to climb 2 steps
            return dp[n];
        }

        if (dp[n] > 0) return dp[n]; // Use cached result if already calculated

        // Recursive case: Ways to climb current step = sum of previous two steps
        dp[n] = GetWaysToClimb(n - 1, dp) + GetWaysToClimb(n - 2, dp);
        return dp[n];
    }
}
```

---

## 📝 Explanation of Code
1. **Dynamic Programming Array (`dp`)**:
   - `dp[i]` stores the number of ways to climb `i` steps.
   - This prevents recalculating results for the same number of steps multiple times.

2. **Base Cases**:
   - `dp[1] = 1`: There's only 1 way to climb 1 step.
   - `dp[2] = 2`: There are 2 ways to climb 2 steps (1 + 1 or 2).

3. **Recursive Logic**:
   - For `n > 2`, the number of ways to climb `n` steps is the sum of ways to climb `n-1` and `n-2` steps.

4. **Optimization**:
   - Check if `dp[n] > 0` to reuse already computed results, reducing the time complexity to **O(n)**.

---

## 🎉 Fun Features
- **Dynamic Programming** ensures the solution is fast and efficient. 🚀
- **Recursive Approach** makes the solution easy to understand and elegant.
- Commented code for readability. 🧑‍💻

---

## 🌟 Let's Connect
If you have any questions or improvements, feel free to open an issue or reach out. Happy coding! 😄
