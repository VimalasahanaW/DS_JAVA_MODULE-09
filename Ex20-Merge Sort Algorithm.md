# Ex20 Sorting an Array using Merge Sort Algorithm
## DATE: 17-11-25
## AIM:
To design a program that sorts a given array of integers in ascending order without using built-in sorting functions, achieving O(n log n) time complexity and minimal space usage.
## Algorithm
1.Divide the array into two halves recursively until you reach subarrays of size 1.

2.Sort the left half and sort the right half by recursively applying merge sort.

3.Merge the two sorted halves by comparing elements and placing them in the correct order.

4.Copy merged elements back into the main array.

5.When all merging is complete, the array is fully sorted in ascending order. 
  

## Program:
```
/*
Program tosorts a given array of integers in ascending order without using built-in sorting functions
Developed by: VIMALA SAHANA W
RegisterNumber: 212223040241  
*/
import java.util.Scanner;

public class MergeSort {

    // Function to merge two halves
    public static void merge(int[] arr, int left, int mid, int right) {
        int n1 = mid - left + 1;
        int n2 = right - mid;

        int[] L = new int[n1];
        int[] R = new int[n2];

        // Copy left half
        for (int i = 0; i < n1; i++)
            L[i] = arr[left + i];

        // Copy right half
        for (int i = 0; i < n2; i++)
            R[i] = arr[mid + 1 + i];

        int i = 0, j = 0, k = left;

        // Merge the two halves
        while (i < n1 && j < n2) {
            if (L[i] <= R[j]) {
                arr[k] = L[i];
                i++;
            } else {
                arr[k] = R[j];
                j++;
            }
            k++;
        }

        // Copy remaining items from L[]
        while (i < n1) {
            arr[k] = L[i];
            i++;
            k++;
        }

        // Copy remaining items from R[]
        while (j < n2) {
            arr[k] = R[j];
            j++;
            k++;
        }
    }

    // Recursive merge sort
    public static void mergeSort(int[] arr, int left, int right) {
        if (left < right) {
            int mid = (left + right) / 2;

            mergeSort(arr, left, mid);      // Sort left half
            mergeSort(arr, mid + 1, right); // Sort right half
            merge(arr, left, mid, right);   // Merge them
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter size of array: ");
        int n = sc.nextInt();

        int[] arr = new int[n];
        System.out.println("Enter array elements:");

        for (int i = 0; i < n; i++) {
            arr[i] = sc.nextInt();
        }

        mergeSort(arr, 0, n - 1);

        System.out.println("Sorted array in ascending order:");
        for (int num : arr) {
            System.out.print(num + " ");
        }

        sc.close();
    }
}

```

## Output:

<img width="483" height="284" alt="image" src="https://github.com/user-attachments/assets/2e4981fa-b8ae-4eb4-96e6-4c641f8039da" />


## Result:
The program has been successfully implemented and executed.
It sorts the given array of integers in ascending order using the Merge Sort algorithm with a time complexity of O(n log n) and minimal extra space.
