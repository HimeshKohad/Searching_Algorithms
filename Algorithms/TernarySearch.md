### ***Ternary Search***

<hr>

Ternary Search is a [_'Divide and Conquer'_](https://github.com/HimeshKohad/Sorting_Algos/blob/main/Algorithms/DivideAndConquer.md) algorithm that can be used to find
an element in an array. It is similar to [_Binary Search_](https://github.com/HimeshKohad/Searching_Algorithms/blob/main/Algorithms/BinarySearch.md) where we divide an
array in 2 parts. But, in this algorithm we divide the array into 3 parts and determine which has the target (key element). 

We can divide the array into 3 parts by taking mid1 and mid2 as shown below:

```
mid1 = l + (r-l)/3 
mid2 = r – (r-l)/3 
```
Initially, l and r will be equal to 0 and n-1 respectively, where n is the length of the array. 

It is same as the [_Binary Search_](https://github.com/HimeshKohad/Searching_Algorithms/blob/main/Algorithms/BinarySearch.md). The only difference is that, here the
time complexity is reduced a bit more. Its time complexity is O(log n base 3) and that of binary search is O(log n base 2).

**Note: The array needs to be sorted in order to apply Ternary Search.**

<hr>

***Steps to perform Ternary Search***

- First, we compare the key with the element at mid1. If found equal, we return mid1.
- If not, then we compare the key with the element at mid2. If found equal, we return mid2.
- If not, then we check whether the key is less than the element at mid1. If yes, then recur to the first part.
- If not, then we check whether the key is greater than the element at mid2. If yes, then recur to the third part.
- If not, then we recur to the second (middle) part.

***Illustration***

![image](https://user-images.githubusercontent.com/107066424/211891908-3ab1c952-fc0e-4bb4-8a01-9e99ed9b5836.png)

<hr>

***Complexity of Ternary Search:***

_Time Complexity:_

| Case | Time Complexity |
|------|------|
|Best Case|O(1)|
|Average Case|O(log3n)|
|Worst Case|O(log3n)|

<br>

_Space Complexity:_ O(1) 

<hr>

***Implementation in C++***

```cpp

#include <iostream>
using namespace std;

int ternarySearch(int l, int r, int key, int ar[])

{
	while (r >= l) {
  
		int mid1 = l + (r - l) / 3;
		int mid2 = r - (r - l) / 3;

		if (ar[mid1] == key) {
			return mid1;
		}
    
		if (ar[mid2] == key) {
			return mid2;
		}

		if (key < ar[mid1]) {

			r = mid1 - 1;
		}
		else if (key > ar[mid2]) {

			l = mid2 + 1;
		}
		else {

			l = mid1 + 1;
			r = mid2 - 1;
		}
	}

	return -1;
}

int main()
{
	int l, r, p, key;

	int ar[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

	l = 0;

	r = 9;

	key = 5;

	p = ternarySearch(l, r, key, ar);

	cout << "Index of "<<key<<" is " << p << endl;

	key = 50;

	p = ternarySearch(l, r, key, ar);

	cout << "Index of "<<key<<" is " << p;
}

```

<hr>

***Implementation in Java***

```java

class Main {

	static int ternarySearch(int l, int r, int key, int ar[])

	{
		while (r >= l) {

			int mid1 = l + (r - l) / 3;
			int mid2 = r - (r - l) / 3;

			if (ar[mid1] == key) {
				return mid1;
			}
			if (ar[mid2] == key) {
				return mid2;
			}

			if (key < ar[mid1]) {
				r = mid1 - 1;
			}
      
			else if (key > ar[mid2]) {
				l = mid2 + 1;
			}
      
			else {
				l = mid1 + 1;
				r = mid2 - 1;
			}
		}

		return -1;
	}

	public static void main(String args[])
	{
		int l, r, p, key;

		int ar[] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };

		l = 0;

		r = 9;

		key = 5;

		p = ternarySearch(l, r, key, ar);

		System.out.println("Index of " + key + " is " + p);

		key = 50;
    
		p = ternarySearch(l, r, key, ar);
    
		System.out.println("Index of " + key + " is " + p);
	}
}

```

<hr>

***Implementation in Python***

```python

def ternarySearch(l, r, key, ar):
	while r >= l:
		
		mid1 = l + (r-l) // 3
		mid2 = r - (r-l) // 3

		if key == ar[mid1]:
			return mid1
      
		if key == mid2:
			return mid2

		if key < ar[mid1]:
			r = mid1 - 1
      
		elif key > ar[mid2]:
			l = mid2 + 1
      
		else:
			l = mid1 + 1
			r = mid2 - 1

	return -1

ar = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

l = 0

r = 9

key = 5

p = ternarySearch(l, r, key, ar)

print("Index of", key, "is", p)

key = 50

p = ternarySearch(l, r, key, ar)

print("Index of", key, "is", p)

```

<hr>

***Binary Search vs. Ternary Search***

While it is true that, the time complexity of ternary search is less than that of binary search, it doesn't mean that ternary search is better. In reality, the number
of comparisons in ternary search are much more, which actually makes it slower than binary search.

