### ***Linear Search***

<hr>

Linear Search is considered as the most Brute Force solution when it comes to searching an element in an array.

A linear search is the simplest approach employed to search for an element in a data set. It examines each element until it finds a match, starting at the beginning of the data set, until the end. The search is finished and terminated once the target element is located. If it finds no match, the algorithm must terminate its execution and return an appropriate result.

The linear search algorithm is easy to implement and efficient in two scenarios:

- When the list contains lesser elements 
- When searching for a single element in an unordered array

<br>

![image](https://user-images.githubusercontent.com/107066424/211307878-c0d2db71-f3d5-4567-9f6d-f424d25e25ba.png)


<hr>

***So how does it work?***

The procedures for implementing linear search are as follows:

Step 1: First, read the search element (Target element) in the array.

Step 2: In the second step compare the Target element with the first element in the array.

Step 3: If both are matched, display "Target is PRESENT" and terminate the Linear Search function. 

Step 4: If both are not matched, compare the search element with the next element in the array. 

Step 5: In this step, repeat steps 3 and 4 until the search (Target) element is compared with the last element of the array.

Step 6: If the last element doesn't match, the Linear Search will be terminated, and the message "Target is ABSENT" will be displayed.

<hr>

***Example:***

Consider an array of size 7 with elements 13, 9, 21, 15, 39, 19, and 27.

Target Elements: 39

<br>

![image](https://user-images.githubusercontent.com/107066424/211307274-ee9f6e67-0138-4a6f-ba2f-3b983fcddb62.png)

<br>

Step 1: The searched element 39 is compared to the first element of an array, which is 13.

![image](https://user-images.githubusercontent.com/107066424/211307371-3c05c84c-24dd-4a79-a584-0ecd8df6bd34.png)

The match is not found, you now move on to the next element and try to implement a comparison.

<br>

Step 2: Now, search element 39 is compared to the second element of an array, 9.

![image](https://user-images.githubusercontent.com/107066424/211307461-6315f22e-0408-4126-bf51-9fdbf43ba70d.png)

As both are not matching, you will continue the search.

<br>

Step 3:  Now, search element 39 is compared with the third element, which is 21.

![image](https://user-images.githubusercontent.com/107066424/211307544-570219f0-6255-4849-b9e4-b5b9ad668208.png)

Again, both the elements are not matching, you move onto the next following element.

<br>

Step 4: Next, search element 39 is compared with the fourth element, which is 15.

![image](https://user-images.githubusercontent.com/107066424/211307637-81827887-1ab0-44fc-9628-4408ba0be40e.png)

As both are not matching, you move on to the next element.

<br>

Step 5: Next, search element 39 is compared with the fifth element 39.

![image](https://user-images.githubusercontent.com/107066424/211307725-0c691502-e15c-4854-b9a9-a3db5e42acc1.png)

A perfect match is found, you stop comparing any further elements and terminate the Linear Search Algorithm and display the element found at location 4.

<hr>

***Algorithm / Pseudocode:***

```cpp
LinearSearch (array arr[], value a)
    Step 1: Set i to 0
    Step 2: if i > n, then go to Step 7 //here n is the number of elements in the array
    Step 3: if arr[i] = a, then go to Step 6
    Step 4: Set i = i + 1
    Step 5: Go to Step 2
    Step 6: Print element a found at index i and go to Step 8
    Step 7: Print element not found and go to Step 8
    Step 8: Exit
```

<hr>

***Complexity of Linear Search:***

_Time Complexity:_

| Case | Time Complexity |
|------|------|
|Best Case|O(1)|
|Average Case|O(n)|
|Worst Case|O(n)|

<br>

_Space Complexity:_ O(n) 

<hr>

***Implementation in C++***

``` cpp
#include <iostream>
using namespace std;

bool linearSearch(int arr[], int n, int target) {

    for (int i = 0; i < n; i++){
        if (arr[i] == target)
            return true;
    }
    return false;
}

int main() {

    int arr[] = {1, 2, 3, 4, 5};
    int n = sizeof(arr)/sizeof(arr[0]);

    int target = 3;

    bool ans = linearSearch(arr, n, target);

    if (ans == true){
        cout << "Target is PRESENT" << endl;
    }

    else {
        cout << "Target is ABSENT" << endl;
    }

}
```

<hr>

***Implementation in Java***

```java

class LinearSearch {
	static int search(int arr[], int n, int target)
	{
		for (int i = 0; i < n; i++) {
			if (arr[i] == target)
				return i;
		}

		return -1;
	}

	public static void main(String[] args)
	{
		int[] arr = { 3, 4, 1, 7, 5 };
		int n = arr.length;
		
		int target = 4;

		int index = search(arr, n, target);
		if (index == -1)
			System.out.println("Element is not present in the array");
		else
			System.out.println("Element found at position " + index);
	}
}


```

<hr>

***Implementation in Python***

```python

def search(arr, x):
 
    for i in range(len(arr)):
 
        if arr[i] == x:
            return i
 
    return -1

```

<hr>

***Applications of Linear Search:***
- Linear search can be applied to both single-dimensional and multi-dimensional arrays.
- Linear search is easy to implement and effective when the array contains only a few elements. 
- Linear Search is also efficient when the search is performed to fetch a single search in an unordered-List.
