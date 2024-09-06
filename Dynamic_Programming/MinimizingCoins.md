# Minimum Number of Coins

The problem of finding the minimum number of coins required to make a desired sum using a set of coin denominations.

## Problem Description

Given a set of coin denominations and a target sum, your task is to determine the minimum number of coins required to make the target sum. If it's not possible to make the target sum with the given coins, return `-1`.

### Input Format
- The first input line contains two integers `n` (number of coins) and `x` (desired sum).
- The second input line contains `n` distinct integers representing the coin denominations.

### Output Format
- Print one integer: the minimum number of coins required. Print `-1` if it's not possible to produce the desired sum.

### Constraints
- `1 <= n <= 100`
- `1 <= x <= 10^6`
- `1 <= c_i <= 10^6`

### Example

#### Input
`3 11` <br>
`1 5 7`

#### Output
`3`


#### Explanation
An optimal solution is `5 + 5 + 1`, which requires `3` coins.

### Solution Overview
- **Dynamic Programming**: We use a DP array where `dp[i]` represents the minimum number of coins needed to make sum `i`.
- **Initialization**: `dp[0]` is initialized to `0` as no coins are needed for a sum of `0`. Other values are set to a large number (`INT_MAX`).
- **Transition**: For each value from `1` to `x`, we update `dp[i]` by considering all coin denominations.
- **Result**: The result is found in `dp[x]`. If `dp[x]` is still `INT_MAX`, print `-1`.

---

## Code Implementations

### C++ Solution

<details>
<summary>Click here to view the <b>C++</b> solution</summary>

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <climits> // For INT_MAX

using namespace std;

int minCoins(int n, int x, const vector<int>& coins) {
    vector<int> dp(x + 1, INT_MAX);
    dp[0] = 0;

    for (int i = 1; i <= x; i++) {
        for (int coin : coins) {
            if (i - coin >= 0 && dp[i - coin] != INT_MAX) {
                dp[i] = min(dp[i], dp[i - coin] + 1);
            }
        }
    }

    return dp[x] == INT_MAX ? -1 : dp[x];
}

int main() {
    int n, x;
    cin >> n >> x;
    vector<int> coins(n);
    
    for (int i = 0; i < n; ++i) {
        cin >> coins[i];
    }

    cout << minCoins(n, x, coins) << endl;

    return 0;
}
```
</details>