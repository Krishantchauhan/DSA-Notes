# Soring


### Bubble
  ```cpp
  void bubbleSort(int arr[], int n)
  {
      for (int i = 0; i < n - 1; i++)
      {
          for (int j = 0; j < n - i - 1; j++)
          {
              if (arr[j] > arr[j + 1])
              {
                  swap(arr[j],arr[j+1]);
              }
          }
      }
  }
  ```
### Selection
  ```cpp
  void selectionSort(int arr[], int n)
  {
      for (int i = 0; i < n - 1; i++)
      {
          int minIndex = i;

          for (int j = i + 1; j < n; j++)
          {
              if (arr[j] < arr[minIndex])
              {
                  minIndex = j;
              }
          }
          swap(arr[i],arr[min]);
      }
  }
  ```
### Insertion
  ```cpp
  void insertionSort(int arr[], int n)
  {
      for (int i = 1; i < n; i++)
      {
          int key = arr[i];
          int j = i - 1;

          while (j >= 0 && arr[j] > key)
          {
              arr[j + 1] = arr[j];
              j--;
          }

          arr[j + 1] = key;
      }
  }
  ```

# Divide and conquer

### Merge Sort

```cpp
void merge(int arr[], int low, int mid, int high)
{
    int leftSize = mid - low + 1;
    int rightSize = high - mid;

    int left[leftSize];
    int right[rightSize];

    for (int i = 0; i < leftSize; i++)
        left[i] = arr[low + i];
    for (int j = 0; j < rightSize; j++)
        right[j] = arr[mid + j + 1];

    int i = 0, j = 0, k = low;

    while (i < leftSize && j < rightSize)
    {
        if (left[i] < right[j])
            arr[k++] = left[i++];
        else
            arr[k++] = right[j++];
    }

    while (i < leftSize)
        arr[k++] = left[i++];

    while (j < rightSize)
        arr[k++] = right[j++];
}

void mergeSort(int arr[], int l, int r)
{
    if (r > l)
    {
        int m = (l + r) / 2;
        mergeSort(arr, l, m);
        mergeSort(arr, m + 1, r);
        merge(arr, l, m, r);
    }
}
```

### Quick

```cpp
int partition(int arr[], int low, int high)
{
    int pivot = arr[high];
    int i = low - 1;

    for (int j = low; j <= high - 1; j++)
    {
        if (arr[j] <= pivot)
        {
            i++;
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
    }

    int temp = arr[i + 1];
    arr[i + 1] = arr[high];
    arr[high] = temp;

    return i + 1;
}

void quickSort(int arr[], int low, int high)
{
    if (low < high)
    {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

```
