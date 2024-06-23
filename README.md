# Sorting
Sorting algorithms implemenation in Java

# Swap/print method
      public static void swap(int[] listToSort, int iIndex, int jIndex) {
        int temp = listToSort[iIndex];
        listToSort[iIndex] = listToSort[jIndex];
        listToSort[jIndex] = temp;
       }
       public static void print(int[] listToSort) {
        for (int el : listToSort) {
            System.out.print(el + ",");
        }
        System.out.println();
    }
    
# Buble Sorting
      public static void bubbleSort(int[] listToSort) {
        for (int i = 0; i < listToSort.length; i++) {
            boolean swapped = false;
            for (int j = listToSort.length - 1; j > i; j--) {
                if (listToSort[j] < listToSort[j - 1]) {
                    swap(listToSort, j, j - 1);
                    swapped = true;
                }
            }
           if (!swapped) {
                break;
            }
        }
    }


# Selection Sorting
      public static void selectionSort(int[] listToSort) {
        for (int i = 0; i < listToSort.length; i++) {
            for (int j = i + 1; j < listToSort.length; j++) {
                if (listToSort[i] > listToSort[j]) {
                    swap(listToSort, i, j);
                }
            }
            print(listToSort);
        }
    }
      
# Insertion Sorting
      for (int i = 0; i < listToSort.length - 1; i++) {
            for (int j = i + 1; j > 0; j--) {
                if (listToSort[j] < listToSort[j - 1]) {
                    swap(listToSort, j, j - 1);
                } else {
                    break;
                }
                print(listToSort);
            }
        

# Shell Sorting
      public static void insertionSort(int[] listToSort, int startIndex, int increment) {
        for (int i = startIndex; i < listToSort.length; i = i + increment) {
            for (int j = Math.min(i + increment, listToSort.length - 1);
                 j - increment >= 0;
                 j = j - increment) {
                if (listToSort[j] < listToSort[j - increment]) {
                    swap(listToSort, j, j - increment);
                } else {
                    break;
                }
                print(listToSort);
            }
        }
    }

    public static void shellSort(int[] listToSort) {
        int increment = listToSort.length / 2;
        while (increment >= 1) {
            for (int startIndex = 0; startIndex < increment; startIndex++) {
                insertionSort(listToSort, startIndex, increment);
            }

            increment = increment / 2;
        }
    }


# Quick Sorting

    public static void quickSort(int[] listToSort, int low, int high) {
        if (low >= high) {
            return;
        }
        int pivotIndex = partition(listToSort, low, high);
        quickSort(listToSort, low, pivotIndex - 1);
        quickSort(listToSort, pivotIndex + 1, high);
    }

    public static int partition(int[] listToSort, int low, int high) {
        int pivot = listToSort[low];
        int l = low;
        int h = high;
        while (l < h) {
            while (listToSort[l] <= pivot && l < h) {
                l++;
            }
            while (listToSort[h] > pivot) {
                h--;
            }
            if (l < h) {
                swap(listToSort, l, h);
            }
        }
        swap(listToSort, low, h);
        System.out.println("Pivot: " + pivot);
        return h;
    }


    
# Merge Sorting

      public static void mergeSort(int[] listToSort) {
        if (listToSort.length == 1) {
            return;
        }

        int midIndex = listToSort.length / 2 + listToSort.length % 2;
        int[] listFirstHalf = new int[midIndex];
        int[] listSecondHalf = new int[listToSort.length - midIndex];
        split(listToSort, listFirstHalf, listSecondHalf);

        mergeSort(listFirstHalf);
        mergeSort(listSecondHalf);

        merge(listToSort, listFirstHalf, listSecondHalf);
        print(listToSort);
    }

    public static void split(int[] listToSort, int[] listFirstHalf, int[] listSecondHalf) {
        int index = 0;
        int secondHalfStartIndex = listFirstHalf.length;
        for (int elements : listToSort) {
            if (index < secondHalfStartIndex) {
                listFirstHalf[index] = listToSort[index];
            } else {
                listSecondHalf[index - secondHalfStartIndex] = listToSort[index];
            }
            index++;
        }
    }

    public static void merge(int[] listToSort, int[] listFirstHalf, int[] listSecondHalf) {
        int mergeIndex = 0;
        int firstHalfIndex = 0;
        int secondHalfIndex = 0;

        while (firstHalfIndex < listFirstHalf.length && secondHalfIndex < listSecondHalf.length) {
            if (listFirstHalf[firstHalfIndex] < listSecondHalf[secondHalfIndex]) {
                listToSort[mergeIndex] = listFirstHalf[firstHalfIndex];
                firstHalfIndex++;
            } else if (secondHalfIndex < listSecondHalf.length) {
                listToSort[mergeIndex] = listSecondHalf[secondHalfIndex];
                secondHalfIndex++;
            }
            mergeIndex++;
        }

        if (firstHalfIndex < listFirstHalf.length) {
            while (mergeIndex < listToSort.length) {
                listToSort[mergeIndex++] = listFirstHalf[firstHalfIndex++];
            }
        }
        if (secondHalfIndex < listSecondHalf.length) {
            while (mergeIndex < listToSort.length) {
                listToSort[mergeIndex++] = listSecondHalf[secondHalfIndex++];
            }
        }
    }

    
