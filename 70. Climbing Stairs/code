public class Solution {
    public int ClimbStairs(int steps) {
        // Step 1: Create an array to store results for subproblems
        int[] waysToClimb = new int[steps + 1];
        waysToClimb[1] = 1; // Base case: Only 1 way to climb 1 step

        // Step 2: Calculate and return the number of ways using helper function
        return CalculateWays(steps, waysToClimb);
    }

    private int CalculateWays(int steps, int[] waysToClimb) {
        if (steps == 1) return waysToClimb[steps]; // If there's 1 step, return 1

        if (steps == 2) {
            waysToClimb[2] = 2; // Base case: 2 ways to climb 2 steps
            return waysToClimb[steps];
        }

        if (waysToClimb[steps] > 0) return waysToClimb[steps]; // Use cached result if already calculated

        // Recursive case: Ways to climb current step = sum of previous two steps
        waysToClimb[steps] = CalculateWays(steps - 1, waysToClimb) + CalculateWays(steps - 2, waysToClimb);
        return waysToClimb[steps];
    }
}
