# DAA-Practicals-
# PRACTICAL - 1
# BUBBLE SORT
#include <iostream>
using namespace std;

class bubblesort {
    int arr[100], size, i, j, temp;

public: 
    void getinput() {
        cout << "Enter the size of the array: ";
        cin >> size;
        cout << "Enter the elements: ";
        for (i = 0; i < size; i++) {
            cin >> arr[i];
        }
    }
    void printelemets() {
        for (i = 0; i < size; i++) { 
            cout << arr[i] << " ";  
        }
        cout << endl;
    }
    void input() {
        for (i = 0; i < size - 1; i++) {
            for (j = 0; j < size - i - 1; j++) { 
                if (arr[j] > arr[j + 1]) {
                    temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;
                }
            }
        }
    }
}; 

int main() { 
    bubblesort bubble;
    bubble.getinput();
        cout << "Before sorting: ";
    bubble.printelemets();
    
  bubble.input();
    
  cout << "Sorted elements: ";
    bubble.printelemets();
        return 0; 
}

# SELECTION SORT
#include <iostream>
using namespace std;

class bubblesort
{
    int arr[100], n, i, j, temp, min;

public:
    void getinput()
    {
        cout << "Enter the size of the array: ";
        cin >> n;
        cout << "Enter the elements: ";
        for (i = 0; i < n; i++)
        {
            cin >> arr[i] ;
        }
    }
    void printelemets()
    {
        for (i = 0; i < n; i++)
        {
            cout << arr[i]<< " " ;
        }
        cout << endl;
    }
    void input()
    {
        for (i = 0; i < n - 1; i++)
        {
            min = i;
            for (j = i+1; j < n; j++)
            {
                if (arr[j] < arr[min])
                {
                    min = j;
                }
            }
            if (min != i)
            {
                temp = arr[i];
                arr[i] = arr[min];
                arr[min] = temp;
            }
        }
    }
};

int main()
{
    bubblesort bubble;
    bubble.getinput();
    cout << "Before sorting: ";
    bubble.printelemets();
    bubble.input();
    cout << "After sorting: ";
    bubble.printelemets();
    return 0;
}

# INSERTION SORT
 #include <iostream>
using namespace std;

class bubblesort
{
    int arr[100], n, i, j, temp, min;

public:
    void getinput()
    {
        cout << "Enter the size of the array: ";
        cin >> n;
        cout << "Enter the elements: ";
        for (i = 0; i < n; i++)
        {
            cin >> arr[i] ;
        }
    }
    void printelemets()
    {
        for (i = 0; i < n; i++)
        {
            cout << arr[i]<< " " ;
        }
        cout << endl;
    }
    void input()
    {
        for (i = 1; i < n; i++)
        {
          temp=arr[i];
          j=i-1;
          while (j>=0 && arr[j>temp]){
            arr[j+1]=arr[j];
            j--;
          }  
            arr[j+1]=temp;        
        }
    }
};

int main()
{
    bubblesort bubble;
    bubble.getinput();
    cout << "Before sorting: ";
    bubble.printelemets();
    bubble.input();
    cout << "After sorting: ";
    bubble.printelemets();
    return 0;
}

# MERGE SORT
#include <iostream>
using namespace std;

class mergesort
{
public:
    int size, arr[100], i;
    void arrayinput()
    {
        cout << "Enter array size: ";
        cin >> size;
        cout << "Enter array elements:\n";
        for (i = 0; i < size; i++)
        {
            cin >> arr[i];
        }
    }
    void printarray()
    {
        for (i = 0; i < size; i++)
        {
            cout << arr[i] << " ";
        }
        cout << endl;
    }
    void merge(int low, int mid, int high)
    {
        int temp[100];
        int i = low, j = mid + 1, k = low;
        while (i <= mid && j <= high)
        {
            if (arr[i] <= arr[j])
            {
                temp[k] = arr[i];
                i++;
            }
            else
            {
                temp[k] = arr[j];
                j++;
            }
            k++;
        }
        while (i <= mid)
        {
            temp[k] = arr[i];
            i++;
            k++;
        }
        while (j <= high)
        {
            temp[k] = arr[j];
            j++;
            k++;
        }
        for (i = low; i <= high; i++)
        {
            arr[i] = temp[i];
        }
    }
    void mergelogic(int low, int high)
    {
        if (low < high)
        {
            int mid = (low + high) / 2;
            mergelogic(low, mid);
            mergelogic(mid + 1, high);
            merge(low, mid, high);
        }
    }
};

int main()
{
    mergesort ms;
    ms.arrayinput();
    cout << "Before sorting: ";
    ms.printarray();
    ms.mergelogic(0, ms.size - 1);
    cout << "After sorting: ";
    ms.printarray();
    return 0;
}

# QUICK SORT 
#include <iostream>
using namespace std;

class quicksort {
    int arr[100], size, i;

public:
    void getinput() {
        cout << "Enter the size of the array: ";
        cin >> size;
        cout << "Enter the elements: ";
        for (i = 0; i < size; i++)
            cin >> arr[i];
    }
    void printelements() {
        for (i = 0; i < size; i++)
            cout << arr[i] << " ";
        cout << endl;
    }
    int partition(int lb, int ub) {
        int pivot = arr[lb];
        int start = lb;
        int end = ub;
        while (start < end) {
            while (start <= ub && arr[start] <= pivot)
                start++;
            while (arr[end] > pivot)
                end--;
            if (start < end)
                swap(arr[start], arr[end]);
        }
        swap(arr[lb], arr[end]);
        return end;
    }
    void quicksort1(int lb, int ub) {
        if (lb < ub) {
            int loc = partition(lb, ub);
            quicksort1(lb, loc - 1);
            quicksort1(loc + 1, ub);
        }
    }
    void sort() {
        quicksort1(0, size - 1);
    }
};

int main() {
    quicksort quick;
    quick.getinput();
    cout << "Before Sorting: ";
    quick.printelements();
    quick.sort();
    cout << "After Sorting: ";
    quick.printelements();
    return 0;
}

# PRACTICAL 2 
# LINEAR SEARCH
#include <iostream>
using namespace std;
int main() {
    int arr[20],n,key,i;
    cout << "Enter the number of elements: ";
    cin >> n;
    cout << "Enter the array elements: ";
    for (int i = 0; i < n; i++) {
        cin >> arr[i];
    }
    cout << "Enter the element to search: ";
    cin >> key;
    for (int i = 0; i < n; i++) {
        if (arr[i] == key) {
            cout << "Element found at index " << i;
            return 0;
        }
    }
    cout << "Element not found";
    return 1;
}

# BINARY SEARCH

#include <iostream>
using namespace std;
int main()
{
    int n, key;
    int low, high, mid;
    cout << "Enter the number of elements: ";
    cin >> n;
    int a[n];
    cout << "Enter the sorted array elements: ";
    for (int i = 0; i < n; i++)
    {
        cin >> a[i];
    }
    cout << "Enter the key element: ";
    cin >> key;
    low = 0;
    high = n - 1;
    while (low <= high)
    {
        mid = (low + high) / 2;
        if (a[mid] == key)
        {
            cout << "Element found at position " << mid << endl;
            break;
        }
        else if (a[mid] < key)
        {
            low = mid + 1;
        }
        else
        {
            high = mid - 1;
        }
    }
    if (low > high)
    {
        cout << "Element not found" << endl;
    }
    return 0;
}

# PRACTICAL-3 
# HEAP SORT (MAX HEAP)
#include <iostream>
using namespace std;

void maxheapify(int arr[], int size, int i)
{
    int largest = i;
    int l = 2 * i;
    int r = 2 * i + 1;
    if (l <= size && arr[l] > arr[largest])
    {
        largest = l;
    }
    if (r <= size && arr[r] > arr[largest])
    {
        largest = r;
    }
    if (largest != i)
    {
        swap(arr[largest], arr[i]);
        maxheapify(arr, size, largest);
    }
}
void heapsort(int arr[], int size)
{
    for (int i = size / 2; i >= 1; i--)
    {
        maxheapify(arr, size, i);
    }
    for (int i = size; i > 1; i--)
    {
        swap(arr[1], arr[i]);
        maxheapify(arr, i - 1, 1);
    }
}
int main()
{
    int n;
    cout << "Enter number of elements: ";
    cin >> n;
    int arr[n + 1];
    cout << "Enter elements: ";
    for (int i = 1; i <= n; i++)
    {
        cin >> arr[i];
    }
    heapsort(arr, n);
    cout << "Sorted array: ";
    for (int i = 1; i <= n; i++)
    {
        cout << arr[i] << " ";
    }
    return 0;
}
# PRACTICAL-4
# FACTORIAL
#include <iostream>
using namespace std;

class factorial {
public:
    int factr(int n) {
        if (n == 0 || n == 1) {
            return 1;
        }
        else {
            int result = n * factr(n - 1);
            return result;
        }
    }
};

int main() {
    factorial obj;
    int n, result;
    cout << "Enter the value to find its factorial: ";
    cin >> n;
    result = obj.factr(n);
    cout << "Factorial of " << n << " is " << result << endl;
    return 0;
}

# RECCURSIVE METHOD 
#include <iostream>
using namespace std;
class factorial{
    public:
    int factr(int n){
    if(n == 0 || n == 1){ 
        return 1;
    }
    else{
    int result = n*factr(n-1);
    return result;
    }
}
};
int main(){
    int n,result;
    factorial obj;
   
 cout << "enter a number:";
    cin>>n;
    result = obj.factr(n);
    cout << "factorial of " << n << " is " << result;
    return 0;
}

