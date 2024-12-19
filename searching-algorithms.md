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
