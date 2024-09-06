# Dice Combinations Problem

Counting the number of ways to construct a sum `n` by throwing a dice one or more times, where each throw produces an outcome between 1 and 6. 

## Problem Description
Given an integer `n`, your task is to count the number of ways to achieve the sum `n` using dice throws. Each dice throw produces an outcome between 1 and 6.

### Input Format
- The only input line contains an integer `n`.

### Output Format
Print the number of ways to achieve the sum `n` modulo \(10^9 + 7\).

### Constraints
- `1 <= n <= 10^6`

### Example
#### Input
`3`
#### Output
`4`


### Solution Overview
- **Dynamic Programming**: We use a DP array where `dp[i]` represents the number of ways to achieve the sum `i`. We initialize `dp[0]` to 1 (base case).
- **Transition**: For each `i` from 1 to `n`, we calculate `dp[i]` by summing up `dp[i - j]` for `j` from 1 to 6, ensuring `i - j` is non-negative.
- **Modulo Operation**: Results are taken modulo \(10^9 + 7\) to handle large numbers.

---

## Code Implementations

<details>
<summary>Click here to view the <b>C++</b> solution</summary>

```cpp
#include<iostream>
#include <vector>
using namespace std;

int DiceCombinations(int N){
    long long mod = 1000000007;
    vector<long long> dp(N+1, 0);
    dp[0] = 1;
    for(int i = 1; i <= N; i++) {
        for(int j = 1; j <= 6 && j <= i; j++) {
            dp[i] = (dp[i] + dp[i-j]) % mod;
        }
    }
    return dp[N];
}

int main()
{
    int n;
    cin >> n;
    cout << DiceCombinations(n) << endl;
    return 0;
}

```
</details>

<details>
<summary>Click here to view the <b>Java</b> solution
</summary>

```java
import java.util.Scanner;

public class DiceCombinations {

    private static final int MOD = 1000000007;

    public static int countWays(int n) {
        long[] dp = new long[n + 1];
        dp[0] = 1;
        
        for (int i = 1; i <= n; i++) {
            for (int j = 1; j <= 6; j++) {
                if (i - j >= 0) {
                    dp[i] = (dp[i] + dp[i - j]) % MOD;
                }
            }
        }
        return (int) dp[n];
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        System.out.println(countWays(n));
    }
}
```
</details>