class Solution {
public:
    int minOperations(vector<int>& nums, int k) {
        int xorResult = k;
        // Calculate the XOR of all elements in nums with k
        for (int num : nums) {
            xorResult ^= num;
        }
      
        // __builtin_popcount returns the number of set bits (1-bits) in an integer
        // which represents the number of different bits from the desired XOR result.
        // This will be the minimum number of operations required to achieve the XOR result k.
        return __builtin_popcount(xorResult);
    }
};
