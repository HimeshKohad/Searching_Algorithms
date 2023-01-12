### ***Jump Search***

<hr>

Like ['Binary Search'](https://github.com/HimeshKohad/Searching_Algorithms/blob/main/Algorithms/BinarySearch.md), Jump Search is a searching algorithm for sorted arrays.
The basic idea is to check fewer elements (than [_'Linear Search'_](https://github.com/HimeshKohad/Searching_Algorithms/blob/main/Algorithms/LinearSearch.md)) by jumping
ahead by fixed steps or skipping some elements in place of searching all elements.

Lets consider a sorted array A[] of size n, with indexing ranging between 0 and n-1, and element x that needs to be searched in the array A[]. 
For implementing this algorithm, a block of size m is also required, that can be skipped or jumped in every iteration. 
Thus, the algorithm works as follows:

- Iteration 1: if (x == A[0]), then success, else, if (x > A[0]), then jump to the next block.
- Iteration 2: if (x == A[m]), then success, else, if (x > A[m]), then jump to the next block.
- Iteration 3: if (x == A[2m]), then success, else, if (x > A[2m]), then jump to the next block.
- At any point in time, if (x < A[km]), then a linear search is performed from index A[ (k - 1)m ] to A[km]

<br>

***Illustration***

![image](https://user-images.githubusercontent.com/107066424/212034301-2e68c986-723f-4ca9-b819-0868de23f794.png)

<hr>

***Optimal Size of m (block size to be skipped)***

The worst-case scenario requires:

- n/m jumps, and
- (m - 1) comparisons (in case of linear search if x < A[km])

Hence, the total number of comparisons will be (n/m + (m - 1)). This expression has to be minimum, so that we get the smallest value of m (block size).

On differentiating this expression with respect to m and equating it with 0, we get:

![image](https://user-images.githubusercontent.com/107066424/212037188-28351411-c4cd-438d-b8b2-2c799d7cf123.png)

Thus, the optimal jump size is √N.

<hr>

***Algorithm of Jump Search***

**Input** will be:
- Sorted array A of size n
- Element to be searched, say _target_

**Output** will be:
- A valid location of _target_ in the array A

<br>

***Steps for Jump Search algorithm***

**Step 1:** Set i=0 and m = √n.

**Step 2:** Compare A[i] with item. If A[i] != item and A[i] < item, then jump to the next block. Also, do the following:

  1. Set i = m
  2. Increment m by √n

**Step 3:** Repeat the step 2 till m < n-1

**Step 4:** If A[i] > item, then move to the beginning of the current block and perform a linear search.

  1. Set x = i
  2. Compare A[x] with item. If A[x]== item, then print x as the valid location else set x++
  3. Repeat Step 4.1 and 4.2 till x < m

**Step 5:** Exit

<hr>

***Complexity of Jump Search:***

_Time Complexity:_

| Case | Time Complexity |
|------|------|
|Best Case|O(1)|
|Average Case|O(√n)|
|Worst Case|O(√n)|

<br>

_Space Complexity:_ O(1) 

<hr>

***Implementation in C++***

```cpp

#include <bits/stdc++.h>
using namespace std;
  
int jumpSearch(int arr[], int x, int n)
{
    int step = sqrt(n);
    int prev = 0;
    
    while (arr[min(step, n) - 1] < x)
    {
        prev = step;
        step += sqrt(n);
        if (prev >= n)
            return -1;
    }
  
    while (arr[prev] < x)
    {
        prev++;
        if (prev == min(step, n))
            return -1;
    }

    if (arr[prev] == x)
        return prev;
  
    return -1;
}
  
int main()
{
    int arr[] = { 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610 };
    int x = 55;
    int n = sizeof(arr) / sizeof(arr[0]);
      
    int index = jumpSearch(arr, x, n);
  
    cout << "\nNumber " << x << " is at index " << index;
    return 0;
}

```

<hr>

***Implementation in Java***

```java

public class JumpSearch
{
    public static int jumpSearch(int[] arr, int x)
    {
        int n = arr.length;

        int step = (int)Math.floor(Math.sqrt(n));

        int prev = 0;
        while (arr[Math.min(step, n) - 1] < x)
        {
            prev = step;
            step += (int)Math.floor(Math.sqrt(n));
            
            if (prev >= n)
                return -1;
        }
  
        while (arr[prev] < x)
        {
            prev++;

            if (prev == Math.min(step, n))
                return -1;
        }
  
        if (arr[prev] == x)
            return prev;
  
        return -1;
    }
  
    public static void main(String[] args)
    {
        int arr[] = { 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610};
        int x = 55;
  
        int index = jumpSearch(arr, x);
  
        System.out.println("\nNumber " + x + " is at index " + index);
    }
}

```

<hr>

***Implementation in Python***

```python

import math
  
def jumpSearch( arr, x, n):
      
    step = math.sqrt(n)
      
    prev = 0
    while arr[int(min(step, n) - 1)] < x:
        prev = step
        step += math.sqrt(n)
        
        if prev >= n:
            return -1
      
    while arr[int(prev)] < x:
        prev += 1
        
        if prev == min(step, n):
            return -1

    if arr[int(prev)] == x:
        return prev
      
    return -1

arr = [ 0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610 ]
x = 55
n = len(arr)

index = jumpSearch(arr, x, n)
  
print("Number" , x, "is at index" ,"%.0f"%index)

```

<hr>

***Key Points to remember:***

- Input array should be sorted.
- Optimal size of the block to be skipped is √n, thus resulting in the time complexity O(√n2).
- The time complexity of this algorithm lies in between linear search (O(n)) and binary search (O(log n)).
- It is also called block search algorithm.

<hr>

***Advantages***

- It is faster than the linear search algorithm which has a time complexity of O(n) for searching an element.

<hr>

***Disadvantages***

- It is slower than binary search algorithm which searches an element in O(log n)
- It requires the input array to be sorted

