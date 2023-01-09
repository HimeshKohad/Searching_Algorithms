### ***Binary Search***

<hr>

The Binary Search Algorithm is a more efficient algorithm than [_'Linear Search'_](https://github.com/HimeshKohad/Searching_Algorithms/blob/main/Algorithms/LinearSearch.md), that is based on the concept of [_'Divide and Conquer'_](https://github.com/HimeshKohad/Sorting_Algos/blob/main/Algorithms/DivideAndConquer.md). It improves the search by recursively dividing the array in half until you find the element or the array gets narrowed down to one element that does'nt match the required Target element.

One requirement for Binary Search is that, the array need to be _sorted_.
The idea of binary search is to use the information that the array is sorted and reduce the time complexity to ***O(Log n)***. 

***Illustration of Binary Search:***

![image](https://user-images.githubusercontent.com/107066424/211372134-d6963284-1ed9-4556-a323-2be9224a6cd8.png)


<hr>

***Algorithm:***

```cpp

BinarySearch (arr[], target, low, high) 
  repeat till low = high
    mid = low + (high - low) / 2
      if (target == arr[mid]) 
      return mid
      
      else if (target > arr[mid]) // target is on the right side
        low = mid + 1
        
      else                       // target is on the left side
        high = mid - 1

```

<hr>

***Complexity of Binary Search:***

_Time Complexity:_

| Case | Time Complexity |
|------|------|
|Best Case|O(1)|
|Average Case|O(logn)|
|Worst Case|O(logn)|

<br>

_Space Complexity:_ O(1) 

<hr>

***Implementation in C++***

```cpp
#include <bits/stdc++.h>
using namespace std;

int BinarySearch(int arr[], int low, int high, int target) {
  while (low <= high) {
    int mid = low + (high - low) / 2;
    
    if (arr[mid] == target) {
      return mid;
    }
    
    else if (arr[mid] < target) {
      low = mid + 1;
    }
    
    else {
      high = mid - 1;
    }
  }
  
  return -1;
}

int main() {
  int arr[] = {2, 3, 5, 7, 9, 10};
  int target = 9;
  
  int n = sizeof(arr) / sizeof(arr[0]);
  
  int res = BinarySearch(arr, 0, n - 1, target);
  
  if (res == -1) {
    cout << "Target is ABSENT" << endl;
  }
    
  else {
    cout << "Target is PRESENT" << endl;
  }
  
  return 0;
}
 
```
