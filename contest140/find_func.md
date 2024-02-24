# Find function Problem


## C++ Solution

```cpp
class Solution {
public:
    long long int solve(int n, vector<long long int>& dp) {
        const long long int MOD = 1000000007LL; // Modulo value
        // Base cases
        if (n == 0) return 2LL % MOD;
        if (n == 1) return 5LL % MOD;
        if (n == 2) return 9LL % MOD;
        if (n == 3) return 7LL % MOD;
        
        // If value already calculated, return it
        if (dp[n] != -1) return dp[n];
        
        // Calculate value based on previous values with modulo applied to each operation
        if (n % 2 == 0) {
            dp[n] = ((solve(n - 2, dp) % MOD) * ((n - 2) % MOD)) % MOD + ((solve(n - 4, dp) % MOD) * ((n - 4) % MOD)) % MOD;
        } else {
            dp[n] = ((solve(n - 1, dp) % MOD) * ((n - 1) % MOD)) % MOD + ((solve(n - 3, dp) % MOD) * ((n - 3) % MOD)) % MOD;
        }
        
        return dp[n] % MOD; // Apply modulo operation before returning
    }
    
    long long int findFun(int n) {
        vector<long long int> dp(n + 1, -1); // Initialize dp array with -1
        return solve(n, dp);
    }
};
