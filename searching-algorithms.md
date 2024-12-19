# Searching
Searching algorithms implemenation in Java

# Linear search
      public static index linearSearch(int[] listToSearch, int target) {
        int n =listToSearch.length, result=-1;
        for(int i=0; i<n; i++){
          if(listToSearch[i] == target){
          result=i;
          break;
          }
          }
          return result;
    }
    
# Binary search
     public static int binarySearch(int[] sortedArray, int number, int min, int max) {
        if (min > max) {
            return -1;
        }

        int mid = min + (max - min) / 2;
        if (sortedArray[mid] == number) {
            return mid;
        }

        if (sortedArray[mid] > number)  {
            return binarySearch(sortedArray, number, min, mid - 1);
        } else {
            return binarySearch(sortedArray, number, mid + 1, max);
        }
    }

    // Binary search function
    public static int binarySearch(int[] arr, int target) {
        int low = 0, high = arr.length - 1;

        while (low <= high) {
            int mid = low + (high - low) / 2; // To avoid overflow

            if (arr[mid] == target) {
                return mid; // Target found
            } else if (arr[mid] < target) {
                low = mid + 1; // Move to the right half
            } else {
                high = mid - 1; // Move to the left half
            }
        }

        return -1; // Target not found
    }

    // Recursive binary search function
    public static int binarySearch(int[] arr, int low, int high, int target) {
        if (low > high) {
            return -1; // Base case: target not found
        }

        int mid = low + (high - low) / 2; // To avoid overflow

        if (arr[mid] == target) {
            return mid; // Target found
        } else if (arr[mid] < target) {
            return binarySearch(arr, mid + 1, high, target); // Search in the right half
        } else {
            return binarySearch(arr, low, mid - 1, target); // Search in the left half
        }
    }
