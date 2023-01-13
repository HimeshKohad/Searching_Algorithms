### ***Exponential Search***

<hr>

Exponential search is also known as _doubling_ or _galloping search_. 
This mechanism is used to find the range where the search key may present. 

It searches for an element in a sorted array by jumping 2^i elements every iteration where i represents the value of loop control variable, 
and then verifying if the search element is present between last jump and the current jump.

If L and U are the upper and lower bound of the list, then L and U both are the power of 2. 
For the last section, the U is the last position of the list. 
For that reason, it is known as exponential.

***Illustration***

<img src = "https://user-images.githubusercontent.com/107066424/212378440-d650a995-f8c1-47c6-ba5b-556127f6b84f.png" alt = "Illustration" width = 500 height = 500/>

<hr>

***How does it work?***

```
1. Jump the array 2^i elements at a time searching for the condition Array[2 ^ (i - 1)] < valueWanted < Array[2^i]. 
   If 2^i is greater than the lenght of array, then set the upper bound to the length of the array.

2. Do a binary search between Array[2 ^ (i - 1)] and Array[2 ^ i]
```

<hr>

***Algorithm***

**Input:** A sorted array, a start and end location and the search key.
**Output:** Location of the key (if found), otherwise wrong location.

```
Begin
   if (end – start) <= 0 then
      return invalid location
   i = 1
   while i < (end - start) do
      if array[i] < key then
         i = i * 2 
      else
         terminate the loop
   done
   call binarySearch(array, i/2, i, key)
End
```

<hr>

***Complexity of Exponential Search:***

_Time Complexity:_

| Case | Time Complexity |
|------|------|
|Best Case|O(1)|
|Average Case|O(log base 2 i)|
|Worst Case|O(log base 2 i)|

where ***i*** is the location where search key is present

<br>

_Space Complexity:_ O(1)

<hr>

***How to find the range where element may be present?***

The idea is to start with subarray size 1, compare its last element with x, then try size 2, then 4 and so on until last element of a subarray is not greater.

Once we find an index i (after repeated doubling of i), we know that the element must be present between i/2 and i 

(Why i/2? because we could not find a greater value in previous iteration)

Given below are the implementations of above steps.

<hr>

***Implementation in C++***

```cpp

#include <bits/stdc++.h>
using namespace std;
  
int binarySearch(int arr[], int, int, int);

int exponentialSearch(int arr[], int n, int x)
{
    if (arr[0] == x)
        return 0;
  
    int i = 1;
    while (i < n && arr[i] <= x)
        i = i * 2;
  
    return binarySearch(arr, i/2, min(i, n - 1), x);
}

int binarySearch(int arr[], int l, int r, int x)
{
    if (r >= l)
    {
        int mid = l + (r - l)/2;

        if (arr[mid] == x)
            return mid;

        if (arr[mid] > x)
            return binarySearch(arr, l, mid - 1, x);

        return binarySearch(arr, mid + 1, r, x);
    }
  
    return -1;
}
  
int main(void)
{
   int arr[] = {2, 3, 4, 10, 40};
   int n = sizeof(arr) / sizeof(arr[0]);
   int x = 10;
   int result = exponentialSearch(arr, n, x);
   (result == -1) ? cout << "Element is not present in array" : cout << "Element is present at index" << result;
   return 0;
}

```

<hr>

***Implementation in Java***

```java

import java.util.Arrays;
  
class Main
{
    static int exponentialSearch(int arr[], int n, int x)
    {
        if (arr[0] == x)
            return 0;
      
        int i = 1;
        while (i < n && arr[i] <= x)
            i = i * 2;
      
        return Arrays.binarySearch(arr, i/2, Math.min(i, n - 1), x);
    }
      
    public static void main(String args[])
    {
        int arr[] = {2, 3, 4, 10, 40};
        int x = 10;
        
        int result = exponentialSearch(arr, arr.length, x);
          
        System.out.println((result < 0) ? "Element is not present in array" : "Element is present at index " + result);
    }
}

```

<hr>

***Implementation in Python***

```python

def binarySearch(arr, l, r, x):
    if r >= l:
        mid = l + (r - l) // 2
          
        if arr[mid] == x:
            return mid
          
        if arr[mid] > x:
            return binarySearch(arr, l, mid - 1, x)

        return binarySearch(arr, mid + 1, r, x)

    return -1
  
def exponentialSearch(arr, n, x):
    if arr[0] == x:
        return 0
          
    i = 1
    
    while i < n and arr[i] <= x:
        i = i * 2
      
    return binarySearch(arr, i // 2, min(i, n - 1), x)
      
arr = [2, 3, 4, 10, 40]
n = len(arr)
x = 10

result = exponentialSearch(arr, n, x)

if result == -1:
    print ("Element not found in the array")
    
else:
    print ("Element is present at index %d" %(result))
    
```

<hr>

***Applications of Exponential Search***

1. Exponential Binary Search is particularly useful for unbounded searches, where size of array is infinite.
2. It works better than Binary Search for bounded arrays, and also when the element to be searched is closer to the first element.
