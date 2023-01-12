### ***Interpolation Search***

<hr>

The Interpolation Search is an improvement over [_Binary Search_](https://github.com/HimeshKohad/Searching_Algorithms/blob/main/Algorithms/BinarySearch.md) for instances, 
where the values in a sorted array are uniformly distributed. 
Interpolation constructs new data points within the range of a discrete set of known data points.

Binary Search always goes to the middle element to check.
On the other hand, interpolation search may go to different locations according to the value of the key being searched.
For example, if the value of the key is closer to the last element, interpolation search is likely to start search toward the end side.

<hr>

***Position Probing in Interpolation Search***

Interpolation search finds a particular item by computing the probe position. 
Initially, the probe position is the position of the middle most item of the collection.

If a match occurs, then the index of the item is returned. To split the list into two parts, we use the following method:

    mid = Lo + ((Hi - Lo) / (A[Hi] - A[Lo])) * (X - A[Lo])

    where −
    A    = list
    Lo   = Lowest index of the list
    Hi   = Highest index of the list
    A[n] = Value stored at index n in the list
    
If the middle item is greater than the item, then the probe position is again calculated in the sub-array to the right of the middle item. 
Otherwise, the item is searched in the subarray to the left of the middle item. 
This process continues on the sub-array as well until the size of subarray reduces to zero.

<hr>

***Algorithm***

As it is an improvisation of the existing Binary Search algorithm, we are mentioning the steps to search the 'target' data value index, using position probing.

```
Step 1 : Start searching data from middle of the list.
Step 2 : If it is a match, return the index of the item, and exit.
Step 3 : If it is not a match, probe position.
Step 4 : Divide the list using probing formula and find the new midle.
Step 5 : If data is greater than middle, search in higher sub-list.
Step 6 : If data is smaller than middle, search in lower sub-list.
Step 7 : Repeat until match.
```

<hr>

***Pseudocode***
```
A → Array list
N → Size of A
X → Target Value

Procedure Interpolation_Search()

   Set Lo  →  0
   Set Mid → -1
   Set Hi  →  N - 1

   While X does not match
   
      if Lo equals to Hi OR A[Lo] equals to A[Hi]
         EXIT: Failure, Target not found
      end if
      
      Set Mid = Lo + ((Hi - Lo) / (A[Hi] - A[Lo])) * (X - A[Lo]) 

      if A[Mid] = X
         EXIT: Success, Target found at Mid
      else 
         if A[Mid] < X
            Set Lo to Mid+1
         else if A[Mid] > X
            Set Hi to Mid - 1
         end if
      end if
   End While

End Procedure
```
<hr>

***Complexity of Interpolation Search:***

_Time Complexity:_

| Case | Time Complexity |
|------|------|
|Best Case|O(1)|
|Average Case|O(log(logn)|
|Worst Case|O(n)|

<br>

_Space Complexity:_ O(1) 

<hr>

***Implementation in C++***

```cpp

#include<bits/stdc++.h>
using namespace std;

int interpolationSearch(int arr[], int n, int x)
{
	int lo = 0, hi = (n - 1);

	while (lo <= hi && x >= arr[lo] && x <= arr[hi])
	{
		if (lo == hi)
		{
			if (arr[lo] == x) return lo;
			return -1;
		}

		int pos = lo + (((double)(hi - lo) / (arr[hi] - arr[lo])) * (x - arr[lo]));

		if (arr[pos] == x)
			return pos;

		if (arr[pos] < x)
			lo = pos + 1;

		else
			hi = pos - 1;
	}
	return -1;
}

int main()
{

	int arr[] = {10, 12, 13, 16, 18, 19, 20, 21, 22, 23, 24, 33, 35, 42, 47};
	int n = sizeof(arr)/sizeof(arr[0]);

	int x = 18; 
	int index = interpolationSearch(arr, n, x);
  
	if (index != -1)
		cout << "Element found at index " << index;
  
	else
		cout << "Element not found.";
  
	return 0;
}

```

<hr>

***Implementation in Java***

```java 

import java.util.*;

class Main {
	public static int interpolationSearch(int arr[], int lo, int hi, int x)
	{
		int pos;

		if (lo <= hi && x >= arr[lo] && x <= arr[hi]) {
			pos = lo + (((hi - lo) / (arr[hi] - arr[lo])) * (x - arr[lo]));

			if (arr[pos] == x)
				return pos;

			if (arr[pos] < x)
				return interpolationSearch(arr, pos + 1, hi, x);

			if (arr[pos] > x)
				return interpolationSearch(arr, lo, pos - 1, x);
		}
    
		return -1;
	}

	public static void main(String[] args)
	{

		int arr[] = { 10, 12, 13, 16, 18, 19, 20, 21, 22, 23, 24, 33, 35, 42, 47 };

		int n = arr.length;

		int x = 18;
		int index = interpolationSearch(arr, 0, n - 1, x);

		if (index != -1)
			System.out.println("Element found at index " + index);
    
		else
			System.out.println("Element not found.");
	}
}

```

<hr>

***Implementation in Python***

```python

def interpolationSearch(arr, lo, hi, x):
  
    if (lo <= hi and x >= arr[lo] and x <= arr[hi]):
    
        pos = lo + ((hi - lo) // (arr[hi] - arr[lo]) * (x - arr[lo]))
  
        if arr[pos] == x:
            return pos

        if arr[pos] < x:
            return interpolationSearch(arr, pos + 1, hi, x)
  
        if arr[pos] > x:
            return interpolationSearch(arr, lo, pos - 1, x)
    return -1
 
arr = [10, 12, 13, 16, 18, 19, 20, 21, 22, 23, 24, 33, 35, 42, 47]
n = len(arr)
  
x = 18
index = interpolationSearch(arr, 0, n - 1, x)
  
if index != -1:
    print("Element found at index", index)
    
else:
    print("Element not found")

```
