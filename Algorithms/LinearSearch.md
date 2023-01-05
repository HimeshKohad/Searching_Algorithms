### ***Linear Search***

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
