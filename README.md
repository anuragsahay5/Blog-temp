# Finding all factors of a number

## Let the number be N, and we need to find all the numbers which divides this number

### Solution 1 : Brute Force
Iterate all numbers between ```1 to N/2``` and find numbers which divides *N ie(N%2==0)*.
<br>
`Code`
```cpp
#include<iostrea>
using namespace std;

int main(){

  int N = 165;
  int n2 = N/2;
  vector<int>factors;

  for(int i=1;i<=n2;i++){
      if(N%i==0)
        factors.push_back(i);
  }

  cout<<"All factors of N are"<<endl;
  for(int &x : factors){
    cout<<x<<" ";
  }

  return 0;
}
```
Time Complexity : O(N) <br>
Space Complexity : O(N)

### An efficient solution can be
Let if a number x divides N then, we can say that y = N/x, which results y*x = N. So y is also a factor of N.<br>
if x<=sqrt(N), then y>=sqrt(N) : if x=sqrt(N) then y is also equal to sqrt(N) <br>
which means, for every x ( x<=sqrt(N) ) which divides N, there exists another factor y ( y>=sqrt(N) ). <br>
so the traversal can be reduced from 1 to N/2, to 1 to sqrt(N).<br>

`Code`

```cpp
#include<iostream>
#include<math.h>
using namespace std;

int main(){

  int N = 165;
  int n = sqrt(N);
  vector<int>factors;
  for(int i=1;i<=n;i++){
      if( N%i==0)
          factors.push_back(i);
      if(i != N/i) // to check if i != sqrt(N)
          factors.push_back(N/i);
  }
  return 0;
}
```
Time Complexity : O(sqrt(N))<br>
Space Complexity : O(N)



