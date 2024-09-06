# Minimum Steps to Reach Zero

This repository contains solutions for finding the minimum number of steps required to reduce a given integer `n` to zero by subtracting one of its digits at each step.

## Problem Description

Given an integer `n`, on each step, you may subtract one of the digits from the number. The goal is to determine the minimum number of steps required to make the number equal to zero.

### Input Format
- The only input line contains an integer `n`.

### Output Format
- Print one integer: the minimum number of steps.

### Constraints
- `1 <= n <= 10^6`

### Example
#### Input
`27`
#### Output
`5`
#### Explanation
An optimal solution is 27 &rarr; 20 &rarr; 18 &rarr; 10 &rarr; 9 &rarr; 0

### Solution Overview
- **Dynamic Programming**: We use a DP array where `dp[i]` represents the minimum number of steps to reduce `i` to zero.
- **Initialization**: `dp[0]` is initialized to `0` as no steps are needed for zero.
- **Transition**: For each number `i`, we calculate `dp[i]` by considering all possible digits that can be subtracted from `i`. We update `dp[i]` by checking the minimum number of steps needed for `i - digit` and adding one step.
- **Result**: The final result is found in `dp[n]`.

---

## Code Implementations

<details>
<summary>Click here to view the <b>C++</b> solution</summary>

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int minSteps(int n) {
    vector<int> dp(n + 1, 1e9);
    dp[0] = 0;
    for (int i = 1; i <= n; i++) {
        int num = i;
        while (num > 0) {
            int digit = num % 10;
            num = num / 10;
            if (digit > 0) {
                dp[i] = min(dp[i], dp[i - digit] + 1);
            }
        }
    }
    return dp[n];
}

int main() {
    int n;
    cin >> n;
    cout << minSteps(n) << endl;
    return 0;
}

```
</details>

<details>
<summary>Click here to view the <b>Java</b> solution
</summary>

```java
import java.util.Scanner;

public class MinStepsToZero {

    private static final int INF = 1000000000;

    public static int minSteps(int n) {
        int[] dp = new int[n + 1];
        for (int i = 1; i <= n; i++) {
            dp[i] = INF;
        }
        dp[0] = 0;

        for (int i = 1; i <= n; i++) {
            int num = i;
            while (num > 0) {
                int digit = num % 10;
                num = num / 10;
                if (digit > 0) {
                    dp[i] = Math.min(dp[i], dp[i - digit] + 1);
                }
            }
        }

        return dp[n];
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        System.out.println(minSteps(n));
    }
}
```
</details>