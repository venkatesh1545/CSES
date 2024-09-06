# Apartment Allocation Problem

This repository contains solutions for distributing apartments to applicants based on their size preferences. The goal is to allocate apartments to as many applicants as possible such that the difference between the desired apartment size and the actual apartment size is within a specified range.

## Problem Description
Given `n` applicants and `m` free apartments, each applicant has a desired apartment size and will accept any apartment whose size is close enough to the desired size. 

### Input Format
- The first input line contains three integers: `n` (number of applicants), `m` (number of apartments), and `k` (maximum allowed difference).
- The second line contains `n` integers representing the desired apartment sizes of the applicants. An applicant will accept any apartment whose size is between `desired_size - k` and `desired_size + k`.
- The third line contains `m` integers representing the sizes of the available apartments.

### Output Format
Print one integer: the number of applicants who will get an apartment.

### Constraints
- `1 <= n, m <= 2 * 10^5`
- `0 <= k <= 10^9`
- `1 <= a_i, b_i <= 10^9`

### Example
#### Input
`4 3 5`<br>
`60 45 80 60`<br>
`30 60 75`

#### Output
`2`


## Solution Overview
- **Sorting**: Both the desired sizes and apartment sizes are sorted.
- **Two-Pointer Technique**: Use a two-pointer technique to efficiently find which apartments fit the desired size ranges of the applicants.

---

## Code Implementations

<details>
<summary>Click here to view the <b>C++</b> solution</summary>

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main() {
    int n, m, k;
    cin >> n >> m >> k;
    vector<int> a(n);
    for (int i = 0; i < n; i++) {
        cin >> a[i];
    }
    vector<int> b(m);
    for (int i = 0; i < m; i++) {
        cin >> b[i];
    }
    sort(a.begin(), a.end());
    sort(b.begin(), b.end());
    
    int cnt = 0;
    int j = 0; 
    for (int i = 0; i < n; i++) {
        while (j < m && b[j] < a[i] - k) {
            j++;
        }
        
        if (j < m && b[j] <= a[i] + k) {
            cnt++;
            j++;
        }
    }
    
    cout << cnt << endl;
    return 0;
}
```
</details>

<details>
<summary>Click here to view the <b>Java</b> solution
</summary>

```java
import java.util.*;

public class ApartmentAllocation {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int m = sc.nextInt();
        int k = sc.nextInt();
        
        int[] a = new int[n];
        int[] b = new int[m];
        
        for (int i = 0; i < n; i++) {
            a[i] = sc.nextInt();
        }
        for (int i = 0; i < m; i++) {
            b[i] = sc.nextInt();
        }
        
        Arrays.sort(a);
        Arrays.sort(b);
        
        int cnt = 0;
        int j = 0;
        for (int i = 0; i < n; i++) {
            
            while (j < m && b[j] < a[i] - k) {
                j++;
            }
            
            if (j < m && b[j] <= a[i] + k) {
                cnt++;
                j++;
            }
        }
        
        System.out.println(cnt);
    }
}
```
</details>