using ll = long long;  // Define 'll' as an alias for 'long long' type
const int MOD = 1e9 + 7;  // The modulo value

class Solution {
public:
    // Function to calculate the sum of minimum elements in every subarray
    int sumSubarrayMins(vector<int>& nums) {
        int length = nums.size();  // Get the number of elements in the array
        vector<int> left(length, -1);  // Create a vector to store indices of previous less element
        vector<int> right(length, length);  // Create a vector to store indices of next less element
        stack<int> stk;  // Stack to help find previous and next less elements
      
        // Finding previous less element for each index
        for (int i = 0; i < length; ++i) {
            while (!stk.empty() && nums[stk.top()] >= nums[i]) {
                stk.pop();  // Pop elements that are greater or equal to current element
            }
            if (!stk.empty()) {
                left[i] = stk.top();  // Store the index of the previous less element
            }
            stk.push(i);  // Push the current index onto the stack
        }
      
        // Clear stack for reuse
        stk = stack<int>();
      
        // Finding next less element for each index
        for (int i = length - 1; i >= 0; --i) {
            while (!stk.empty() && nums[stk.top()] > nums[i]) {
                stk.pop();  // Pop elements that are strictly greater than current element
            }
            if (!stk.empty()) {
                right[i] = stk.top();  // Store the index of the next less element
            }
            stk.push(i);  // Push the current index onto the stack
        }
      
        ll sum = 0;  // Initialize the sum of minimum elements in all subarrays
      
        // Calculating the contribution of each element to the overall sum
        for (int i = 0; i < length; ++i) {
            sum += static_cast<ll>(i - left[i]) * (right[i] - i) * nums[i] % MOD;
            sum %= MOD;  // Apply modulus to keep the sum within range
        }
      
        return sum;  // Return the sum of minimums of all subarrays
    }
};
