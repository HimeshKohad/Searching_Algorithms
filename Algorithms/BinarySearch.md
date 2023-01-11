### ***Binary Search***

<hr>

The Binary Search Algorithm is a more efficient algorithm than [_'Linear Search'_](https://github.com/HimeshKohad/Searching_Algorithms/blob/main/Algorithms/LinearSearch.md), that is based on the concept of [_'Divide and Conquer'_](https://github.com/HimeshKohad/Sorting_Algos/blob/main/Algorithms/DivideAndConquer.md). It improves the search by recursively dividing the array in half until you find the element or the array gets narrowed down to one element that does'nt match the required Target element.

One requirement for Binary Search is that, the array need to be _sorted_.
The idea of binary search is to use the information that the array is sorted and reduce the time complexity to ***O(Log n)***. 

<br>

***Real-life Examples of Binary Search:***
- The major example of binary search is the way we use dictionaries. To find a word, we randomly check for a word and move based on that word.
- Similarly, to find the minimum ad maximum size that is needed for an office to accommodate the staff we can easily do a binary search to arrive at the size by halving the available list.
- Selecting students based on height when the students are not particularly aware of their height.
- Checking for books in a library as books are arranged in order.
- Opening a page number in a book in random order.
- Accessing student’s information in a university database. This is very helpful because generally information is sorted and stored and since there would be a huge number of student’s information at the first step itself dataset is halved.

<hr>

***Illustration of Binary Search:***

![image](https://user-images.githubusercontent.com/107066424/211372134-d6963284-1ed9-4556-a323-2be9224a6cd8.png)

<br>

***Iteration 1:***

Array: {2, 5, 8, 12, 16, 23, 38, 56, 72, 91}

Select the middle element. (here 16)

Since 23 is greater than 16, so we divide the array into two halves and consider the sub-array after element 16.

Now this subarray with the elements after 16 will be taken into the next iteration.

<br>

***Iteration 2:*** 

Array: {23, 38, 56, 72, 91}

Select the middle element. (now 56)

Since 23 is smaller than 56, so we divide the array into two halves and consider the sub-array before element 56.

Now this subarray with the elements before 56 will be taken into next iteration.

<br>

***Iteration 3:***

Array: {23, 38}

Select the middle element. (now 23)

Since 23 is the middle element. So the iterations will now stop.

Let’s say the iteration in Binary Search terminates after k iterations. In the above example, it terminates after 3 iterations, so here k = 3.

At each iteration, the array is divided by half. So let’s say the length of the array at any iteration is n.

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

<hr>

***Implementation in Java***

```java

class BinarySearch
{

	int binarySearch(int arr[], int l, int r, int x)
	{
		if (r>=l)
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

	public static void main(String args[])
	{
		BinarySearch ob = new BinarySearch();
		int arr[] = {2, 3, 4, 10, 40};
		int n = arr.length;
		int x = 10;
    
		int result = ob.binarySearch(arr, 0, n - 1, x);
    
		if (result == -1)
			System.out.println("Element not present");
      
		else
			System.out.println("Element found at index " + result);
	}
}


```

<hr>

***Implementation in Python***

```python

def binary_search(arr, x):
	low = 0
	high = len(arr) - 1
	mid = 0

	while low <= high:

		mid = (high + low) // 2

		if arr[mid] < x:
			low = mid + 1

		elif arr[mid] > x:
			high = mid - 1

		else:
			return mid

	return -1

arr = [ 2, 3, 4, 10, 40 ]
x = 10

result = binary_search(arr, x)

if result != -1:
	print("Element is present at index", str(result))
else:
	print("Element is not present in array")

```

<hr>

***Advantages of Binary Search:***

- Instead of searching the whole lo, in the first step itself half of the search list is eliminated.
- It is easy to identify whether the element that is being searched is before or after the position of the current element in the list.
- This can be easily used to reduce the search and improve the speed.
- When compared to linear search it is more efficient in searching data in a large list.
- It is possible to identify in each step, which sub-tree contains the desired element.
- It is more efficient than arrays and linked lists.
- The deletion and insertion take place quickly when compared with other data structures such as linked lists or arrays.

<br>

***Disadvantages of Binary Search:***

- Since the recursive method is used for searching more stack space is required which is a major disadvantage
- This technique is much more prone to errors and difficult to debug in case of errors
- This provides poor caching of memory.
- It is very much time-consuming because of recursive calls.
