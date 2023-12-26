class Solution {
public:
    // Function to calculate the number of distinct ways to roll the dice
    // such that the sum of the face-up numbers equals to 'target'
    int numRollsToTarget(int numberOfDice, int faces, int targetSum) {
        const int MODULO = 1e9 + 7; // Modulo for avoiding integer overflow

        // Create a dynamic programming table initialized with zeros,
        // `dp[currentTarget]` will represent the number of ways to get sum `currentTarget`
        vector<int> dp(targetSum + 1, 0);

        // Base case: one way to reach sum 0 - by not choosing any dice
        dp[0] = 1;

        // Iterate over the number of dice
        for (int i = 1; i <= numberOfDice; ++i) {
            // Temporary vector to store ways to reach a certain sum with the current dice
            vector<int> newDp(targetSum + 1, 0);

            // Calculate number of ways to get each sum from 1 to `targetSum` with `i` dice
            for (int currentSum = 1; currentSum <= min(targetSum, i * faces); ++currentSum) {
                // Look back at most `faces` steps to find the number of ways to
                // reach the current sum from previous sums using different face values
                for (int faceValue = 1; faceValue <= min(currentSum, faces); ++faceValue) {
                    newDp[currentSum] = (newDp[currentSum] + dp[currentSum - faceValue]) % MODULO;
                }
            }

            // Move the updated values in `newDp` to `dp` for the next iteration
            dp = move(newDp);
        }

        // Final answer is the number of ways to reach `targetSum` with `numberOfDice` dice
        return dp[targetSum];
    }
};
