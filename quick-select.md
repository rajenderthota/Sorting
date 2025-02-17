### **Quickselect Algorithm in Java for Rank Selection**
The **Quickselect** algorithm is a variation of **Quicksort** that efficiently finds the k-th smallest (or largest) element in an unsorted array. It has an **average time complexity of O(N)** but a worst-case of **O(N²)** (though rare with good pivot selection).

---

### **Quickselect for Rank Selection**
- **Problem:** Given an unsorted array, find the element at the **k-th rank** (1-based index).
- **Approach:** 
  - Use the **partitioning** step from Quicksort.
  - Recursively search only in the relevant half (unlike Quicksort, which sorts both halves).
  - Base case: If pivot index matches \( k-1 \), return the pivot element.

---

### **Java Implementation**
```java
import java.util.Random;

public class QuickSelect {
    // Function to find the k-th smallest element
    public static int quickSelect(int[] arr, int left, int right, int k) {
        if (left == right) return arr[left]; // Base case

        int pivotIndex = partition(arr, left, right); // Partition the array

        if (pivotIndex == k) return arr[pivotIndex]; // Found the k-th smallest element
        else if (pivotIndex > k) return quickSelect(arr, left, pivotIndex - 1, k); // Search left
        else return quickSelect(arr, pivotIndex + 1, right, k); // Search right
    }

    // Lomuto Partition Scheme (chooses last element as pivot)
    private static int partition(int[] arr, int left, int right) {
        int pivot = arr[right]; 
        int i = left; // Index for smaller elements

        for (int j = left; j < right; j++) {
            if (arr[j] < pivot) { // Move smaller elements to the left
                swap(arr, i, j);
                i++;
            }
        }
        swap(arr, i, right); // Place pivot in its correct position
        return i;
    }

    private static void swap(int[] arr, int i, int j) {
        int temp = arr[i];
        arr[i] = arr[j];
        arr[j] = temp;
    }

    // Driver method
    public static void main(String[] args) {
        int[] arr = {7, 10, 4, 3, 20, 15};
        int k = 3; // Find the 3rd smallest element

        int kthSmallest = quickSelect(arr, 0, arr.length - 1, k - 1); // k-1 for 0-based index
        System.out.println("The " + k + "rd smallest element is: " + kthSmallest);
    }
}
```

---

### **Explanation**
1. **Initial Array:** `[7, 10, 4, 3, 20, 15]`
2. **Quickselect Execution:**
   - Select a pivot (last element in this case).
   - Partition the array around the pivot.
   - Recursively search only in the half where the k-th element lies.
3. **Final Output:** `The 3rd smallest element is: 7`

---

### **Time Complexity**
- **Best/Average Case:** \(O(N)\) (Linear)
- **Worst Case:** \(O(N^2)\) (When the pivot is always the largest or smallest element)

---

### **Optimizations**
- **Randomized Pivot Selection**: Instead of always picking the last element, pick a random index to reduce worst-case probability.
```java
private static int partitionRandom(int[] arr, int left, int right) {
    Random rand = new Random();
    int pivotIndex = left + rand.nextInt(right - left + 1);
    swap(arr, pivotIndex, right); // Move pivot to the end
    return partition(arr, left, right);
}
```

---

### **Use Cases**
- **Finding the k-th smallest or largest element** in an unsorted array.
- **Median Selection**: Median Selection: k=N/2​ gives the median.
- **Top K Elements Problems** (modification required).
