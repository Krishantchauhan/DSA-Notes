# BS

- ## Normal Code
    ```cpp
    int binse(int a[], int size, int key)
    {
      int low = 0, high = size - 1;
      while (low <= high)
      {
        int mid = (low + high) / 2;
        if (key == a[mid])
          return mid + 1;
        else if (a[mid] > key)
          high = mid - 1;
        else
          low = mid + 1;
      }
      return -1;
    }
    ```
    

- ## Reverse Sorted
    
    ```cpp
    int reverseBinarySearch(const std::vector<int>& arr, int target) {
        int left = 0;
        int right = arr.size() - 1;
    
        while (left <= right) {
            int mid = left + (right - left) / 2;
    
            if (arr[mid] == target) {
                return mid;  // Element found at index mid
            } else if (arr[mid] > target) {
                left = mid + 1;  // Search in the left half
            } else {
                right = mid - 1;  // Search in the right half
            }
        }
    
        return -1;  // Element not found
    }
    ```
    
- ## First Occurrence
    
    ```cpp
    int firstocc(int a[], int n, int key)
    {
        int low = 0, high = n - 1, pos = -1;
    
        while (low <= high)
        {
            int mid = low + (high - low) / 2;
    
            if (arr[mid] == key)
            {
                pos = mid;
                high = mid - 1;
            }
            else if (arr[mid] < key)
                low = mid + 1;
            else
                high = mid - 1;
        }
    
        return pos;
    }
    ```
    
- ## Last Occurrence
    
    ```cpp
    int lasttocc(int a[], int n, int key)
    {
        int low = 0, high = n - 1, pos = -1;
    
        while (low <= high)
        {
            int mid = low + (high - low) / 2;
            (*ct)++;
    
            if (arr[mid] == key)
            {
                pos = mid;
                low = mid + 1;
            }
            else if (arr[mid] < key)
                low = mid + 1;
            else
                high = mid - 1;
        }
    
        return pos;
    }
    ```
    
- ## Count Occurrence
    
    ```cpp
    int countfun(int a[], int size, int key)
    {
        int first = firstocc(a, size, key);
        if (first == -1)
            return 0;
        else
    	     count = last - first+1;
    	     return count;
    }
    ```
    
- ## Count Rotation
    
    ```cpp
    int binse(int a[], int size)
    {
        int low = 0, high = size - 1;
        while (low <= high)
        {
            int mid = low + (high - low) / 2;
    
            int nxt = (mid + 1) % size;
            int prev = (mid + size - 1) % size;
    
            if (a[mid] <= a[nxt] && a[mid] <= a[prev])
                return a[mid]; // Return the minimum element
            else if (a[low] <= a[mid])
                low = mid + 1;
            else if (a[high] <= a[mid])
                high = mid - 1;
        }
        return a[0]; // Fallback if the array is not rotated
    }
    ```
    
- ## Floor
    
    ```cpp
    int findFloor(vector<int> &nums, int target)
    {
        int low = 0, high = nums.size() - 1;
        int floor = -1;
    
        while (low <= high)
        {
            int mid = low + (high - low) / 2;
            if (nums[mid] < target)
            {
                low = mid + 1;
            }
            else if (nums[mid] > target)
            {
                floor = nums[mid];
                high = mid - 1;
            }
        }
    
        return floor;
    }
    ```
    
- ## Ceiling
    
    ```cpp
    int findFloor(vector<int> &nums, int target) {
        int low = 0, high = nums.size() - 1;
        int floor = -1;
    
        while (low <= high) {
            int mid = low + (high - low) / 2;
            if (nums[mid] < target) {
                low = mid + 1;
            } else if (nums[mid] > target) {
                floor = nums[mid];
                high = mid - 1;
            }
        }
    
        return floor;
    }
    ```
    


#  Templates
 



```cpp
//New way but complicated
int bs() {
    int low = 0, high = n - 1; 
    while(low < high) {
        int mid = low + (high - low) / 2;
        if(nums[mid]<nums[high]) //condition
            high = mid;
        else 
            low = mid + 1;
    }
    return low;
}
```

```cpp

//Binary Search
int bs(int a[], int size, int key)
{
    int low = 0, high = n - 1;
    while (low <= high)
    {
        int mid = low + (high - low) / 2;
        if (arr[mid] == key)
          return mid
        else if (arr[mid] < key)
            low = mid + 1;
        else
            high = mid - 1;
    }
    return -1;
}
```

```cpp
//Recursion
int bs(vector<int>& nums,int low,int high){
        if(low<high){
            int mid=low+(high-low)/2;
            if(nums[mid]<nums[high])
                return bs(nums,low,mid);
            return bs(nums,mid+1,high);
        }
        return nums[low];
    }
```
