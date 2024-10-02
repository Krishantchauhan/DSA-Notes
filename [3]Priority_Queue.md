# Heap

Here's an example of how to implement a max heap in C++ using the `<queue>` library:

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main() {
    //  max heap
    priority_queue<int> max_heap;

    max_heap.push(5);
    max_heap.push(3);
    max_heap.push(8);
    max_heap.push(1);

    // print the maximum value in the heap
    cout << max_heap.top() << endl; // Output: 8

    // remove and return the maximum value from the heap
    max_heap.pop();
    cout << max_heap.top() << endl; // Output: 5

    return 0;
}

```

This code creates an empty max heap using the `priority_queue` class from the `<queue>` library. The `push()` function is used to insert values into the heap, and the `top()` function is used to access the maximum value in the heap. The `pop()` function is used to remove and return the maximum value from the heap.



## Kth Smallest Element

- Dry Run
  ```jsx
  Initial Priority Queue: []

  1. First iteration (i = 0):
     Element: 7
     pq.push(7)
     pq: [7] (size: 1, less than k)

     [7]

  2. Second iteration (i = 1):
     Element: 10
     pq.push(10)
     pq: [10, 7] (size: 2, less than k)

     [10]
      |
     [ 7]

  3. Third iteration (i = 2):
     Element: 4
     pq.push(4)
     pq: [10, 7, 4] (size: 3, equal to k)

     [10]
      |
     [ 7]
      |
     [ 4]

  4. Fourth iteration (i = 3):
     Element: 3
     pq.push(3)
     pq: [10, 7, 4, 3] (size: 4, greater than k)
     pq.pop()  -> removes 10 (largest element)
     pq: [7, 3, 4]

         [7]
          |
         [ 3]
          |
         [ 4]

  5. Fifth iteration (i = 4):
     Element: 20
     pq.push(20)
     pq: [20, 7, 4, 3] (size: 4, greater than k)
     pq.pop()  -> removes 20 (largest element)
     pq: [7, 3, 4]

         [7]
          |
         [ 3]
          |
         [ 4]

  6. Sixth iteration (i = 5):
     Element: 15
     pq.push(15)
     pq: [15, 7, 4, 3] (size: 4, greater than k)
     pq.pop()  -> removes 15 (largest element)
     pq: [7, 3, 4]

         [7]
          |
         [ 3]
          |
         [ 4]

  Final Priority Queue: [7, 3, 4]
  ```

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main()
{
    int arr[6] = {7, 10, 4, 3, 20, 15};
    int k = 3;

    priority_queue<int> pq;

    cout << "Array: ";
    for (auto i : arr)
    {
        cout << i << ' ';
    }
    cout << endl;

    for (int i = 0; i < 6; i++)
    {
        pq.push(arr[i]);
        if (pq.size() > k)
            pq.pop();
    }

    cout << pq.top();

    return 0;
}
```

## Kth Largest Element

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main()
{
    int arr[6] = {7, 10, 4, 3, 20, 15};
    int k = 3;

    priority_queue<int, vector<int>, greater<int> > pq;

    cout << "Array: ";
    for (auto i : arr)
    {
        cout << i << ' ';
    }
    cout << endl;

    for (int i = 0; i < 6; i++)
    {
        pq.push(arr[i]);
        if (pq.size() > k)
            pq.pop();
    }
        cout << pq.top()<<" ";
    return 0;
}
```

## Kth Smallest Elements

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main()
{
    int arr[6] = {7, 10, 4, 3, 20, 15};
    int k = 3;

    priority_queue<int> pq;

    cout << "Array: ";
    for (auto i : arr)
    {
        cout << i << ' ';
    }
    cout << endl;

    for (int i = 0; i < 6; i++)
    {
        pq.push(arr[i]);
        if (pq.size() > k)
            pq.pop();
    }

    while (!pq.empty())
    {
        cout << pq.top() << " ";
        pq.pop();
    }

    return 0;
}
```

## Kth Greater Elements

```cpp
#include <iostream>
#include <queue>
using namespace std;

int main()
{
    int arr[6] = {7, 10, 4, 3, 20, 15};
    int k = 3;

    priority_queue<int, vector<int>, greater<int> > pq;

    cout << "Array: ";
    for (auto i : arr)
    {
        cout << i << ' ';
    }
    cout << endl;

    for (int i = 0; i < 6; i++)
    {
        pq.push(arr[i]);
        if (pq.size() > k)
            pq.pop();
    }
    while (!pq.empty())
    {
        cout << pq.top()<<" ";
        pq.pop();
    }
    return 0;
}
```

## sort-k-sorted-array

```cpp
// Doing Using Min Heap and getting complexity NlogK;

#include <iostream>
#include <queue>
using namespace std;

int main()
{
    int arr[7] = {6, 5, 3, 2, 8, 10, 9};
    int k = 3;

    priority_queue<int, vector<int>, greater<int>> pq;

    cout << "Array: ";
    for (auto i : arr)
    {
        cout << i << ' ';
    }
    cout << endl;

    vector<int> ans;

    for (int i = 0; i < 7; i++)
    {
        pq.push(arr[i]);
        if (pq.size() > k)
        {
            ans.push_back(pq.top());
            pq.pop();
        }
    }

    while (!pq.empty())
    {
        ans.push_back(pq.top());
        pq.pop();
    }

    for (int i = 0; i < 7; i++)
    {
        cout << ans[i] << " ";
    }

    return 0;
}
```

## K Closest Number

```cpp
#include <iostream>
#include <vector>
#include <queue>
#include <algorithm>

using namespace std;

vector<int> findClosestElements(vector<int> &arr, int k, int x)
{
    priority_queue<pair<int, int> > pq;
    vector<int> ans;

    for (int i = 0; i < arr.size(); i++)
    {
        int diff = abs(arr[i] - x);
        pq.push(make_pair(diff, arr[i]));
        if (pq.size() > k)
            pq.pop();
    }

    while (!pq.empty())
    {
        ans.push_back(pq.top().second);
        pq.pop();
    }

    sort(ans.begin(), ans.end());
    return ans;
}

int main()
{
    vector<int> arr;
    arr.push_back(5);
    arr.push_back(6);
    arr.push_back(7);
    arr.push_back(8);
    arr.push_back(9);

    int k = 3;
    int x = 7;

    vector<int> closestElements = findClosestElements(arr, k, x);

    cout << "Closest Elements: ";
    for (int num : closestElements)
    {
        cout << num << " ";
    }
    cout << endl;

    return 0;
}
```
