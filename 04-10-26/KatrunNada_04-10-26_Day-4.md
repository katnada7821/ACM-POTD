# Day-4-#1[32-A-Reconnaissance]
## Problem Description
heights can differ by at most d centimeters.how many ways exist to form a reconnaissance unit of two soldiers from his detachment.
## Approach-
1.Using two pointer and getting the j farthest from i and then multiplying the distance by 2 as 1, 2) and (2, 1) should be regarded as different.
## Complexity-
Time: O(n log n) .
Space: O(1) .

## Code-
```cpp
#include <bits/stdc++.h>
using namespace std;
int main(){
    int n;
    long long d;
    cin>>n>>d;
    vector<long long> a(n);
    for(int i=0;i<n;i++){
        cin>>a[i];
    }
    sort(a.begin(),a.end());
    long long cnt=0;
    int j=0;
    for(int i=0;i<n;i++){
        while(j+1<n&&a[j+1]-a[i]<=d){
            j++;
        }
        cnt+=2LL*(j-i);

        
            
        
    }
    cout<<cnt;
    return 0;
}
```
## Accepted Submission
![Accepted Submission](32A_Accepted.png)
