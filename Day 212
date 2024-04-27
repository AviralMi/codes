class Solution {
public:
    int findRotateSteps(string ring, string key) {
        int keyLength = key.size();               // Length of the key
        int ringLength = ring.size();             // Length of the ring
        vector<int> position[26];                 // Array of vectors to hold the positions of each character
      
        // Populate the position array with the indices of each character in the ring
        for (int i = 0; i < ringLength; ++i) {
            position[ring[i] - 'a'].push_back(i);
        }

        // Initialize the dynamic programming table, f, with infinity
        int dpTable[keyLength][ringLength];
        memset(dpTable, 0x3f, sizeof(dpTable));

        // Base case: fill in the first row of the dynamic programming table
        for (int index : position[key[0] - 'a']) {
            dpTable[0][index] = min(index, ringLength - index) + 1;
        }

        // Fill in the remainder of the dp table
        for (int i = 1; i < keyLength; ++i) {
            for (int j : position[key[i] - 'a']) {
                for (int k : position[key[i - 1] - 'a']) {
                    int stepDiff = min(abs(j - k), ringLength - abs(j - k)) + 1; // Calculate the minimum steps
                    dpTable[i][j] = min(dpTable[i][j], dpTable[i - 1][k] + stepDiff);
                }
            }
        }

        // Find the minimum steps needed to spell the last character of the key
        int minSteps = INT_MAX;
        for (int index : position[key[keyLength - 1] - 'a']) {
            minSteps = min(minSteps, dpTable[keyLength - 1][index]);
        }

        // Return the minimum steps to spell all characters in the key
        return minSteps;
    }
};
