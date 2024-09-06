# Distinct Numbers Problem

This repository contains the solution for counting distinct numbers in both C++ and Java. You can view the code in either language by tapping on the respective tabs below.

## Problem Description
Given an array of `n` integers, our task is to find how many distinct numbers are there in the array.

###Input Format <br>
The first input line has an integer n: the number of values.
The second line has n integers x1,x2,....,xn.

### Output Format <br>
Print one integers: the number of distinct values.

### Constraints

- 1 <= n <= 2*10^5
- 1 <= xi <= 10^9
### Example
#### Input:
`5`
<br>
`
2 3 2 2 3
`
#### Output:
`2`

### Solution Overview:
- We sort the array.
- We then count how many numbers are different from their predecessor.
- Finally, we return the count of distinct numbers.

---

## Code Implementations

<details>
<summary>Click here to view the <b>C++</b> solution
</summary>

```cpp
#include <iostream>
#include<vector>
#include<algorithm>
using namespace std;

int main() {
    int n, answer = 0;
    cin >> n;
    vector<int> values(n);
    for (int i = 0; i < n; i++) {
        cin >> values[i];
    }
    sort(values.begin(), values.end());
    for (int i = 1; i < n; i++) {
        if (values[i] != values[i - 1]) {
            answer++;
        }
    }
    cout << answer + 1 << endl;
}
```
</details>

<details>
<summary>Click here to view the <b>Java</b> solution
</summary>

```java
import java.util.*;

public class DistinctNumbers {
    public static void main(String[] args) {
        try (Scanner sc = new Scanner(System.in)) {
            int n = sc.nextInt();
            int[] a = new int[n];
            for (int i = 0; i < n; i++) {
                a[i] = sc.nextInt();
            }
            Arrays.sort(a);
            int ans = 0;
            for (int i = 1; i < n; i++) {
                if (a[i] != a[i-1]) {
                    ans++;
                }
            }
            System.out.println(ans + 1);
        }
    }
}
