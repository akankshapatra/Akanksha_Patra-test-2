# DSA Homework Answers

## Q1. Linear Search Trace
Array: {14, 52, 7, 38, 21, 63, 45}  
Target: 63  

| Step | Index | Value Checked | Match? |
|------|-------|---------------|--------|
| 1    | 0     | 14            | No     |
| 2    | 1     | 52            | No     |
| 3    | 2     | 7             | No     |
| 4    | 3     | 38            | No     |
| 5    | 4     | 21            | No     |
| 6    | 5     | 63            | Yes → Found |

- **Q1a. Found at index:** 5  
- **Q1b. Total steps taken:** 6  
- **Q1c. Case type:** Average Case (found in the middle, not first or last)

---

## Q2. Binary Search Trace
Array: {6, 14, 23, 39, 47, 55, 72}  
Target: 23  

| Step | Left | Right | Mid | Value at Mid | Decision |
|------|------|-------|-----|--------------|----------|
| 1    | 0    | 6     | 3   | 39           | 23 < 39 → Search Left half |
| 2    | 0    | 2     | 1   | 14           | 23 > 14 → Search Right half |
| 3    | 2    | 2     | 2   | 23           | Found! |

- **Q2a. Found at index:** 2  
- **Q2b. Total steps (Binary Search):** 3  
- **Q2c. Total steps (Linear Search):** 3  
- **Q2d. Faster?** Binary Search, because it halves the search space each step.

---

## Q3. Bubble Sort Trace
Array: {38, 15, 42, 6, 29}  

**Pass 1**
| Step | Elements Compared | Swap? | Array After Step |
|------|-------------------|-------|------------------|
| 1    | 38 & 15           | Yes   | {15, 38, 42, 6, 29} |
| 2    | 38 & 42           | No    | {15, 38, 42, 6, 29} |
| 3    | 42 & 6            | Yes   | {15, 38, 6, 42, 29} |
| 4    | 42 & 29           | Yes   | {15, 38, 6, 29, 42} |

➡ After Pass 1, **42** is settled at the end.

**Pass 2**
| Step | Elements Compared | Swap? | Array After Step |
|------|-------------------|-------|------------------|
| 1    | 15 & 38           | No    | {15, 38, 6, 29, 42} |
| 2    | 38 & 6            | Yes   | {15, 6, 38, 29, 42} |
| 3    | 38 & 29           | Yes   | {15, 6, 29, 38, 42} |

➡ After Pass 2, **38** is settled at the end.

---

## Q4. Linear Search Code
```java
public class MyLinearSearch {
    public static void main(String[] args) {
        int[] arr = {33, 8, 71, 19, 56, 44, 27};
        int target = 56;

        int steps = 0;
        boolean found = false;

        for (int i = 0; i < arr.length; i++) {
            steps++;
            System.out.println("Checking index " + i + " value " + arr[i]);

            if (arr[i] == target) {
                System.out.println("Found at index " + i);
                found = true;
                break;
            }
        }

        if (!found) {
            System.out.println("Not Found");
        }

        System.out.println("Total Steps = " + steps);
    }
}
```
## Q2. Binary Search Trace
```java 
public class MyBinarySearch {
    public static void main(String[] args) {
        int[] arr = {9, 21, 34, 48, 57, 66, 83};
        int target = 66;

        int left = 0;
        int right = arr.length - 1;
        int steps = 0;
        boolean found = false;

        while (left <= right) {
            steps++;
            int mid = (left + right) / 2;
            System.out.println("Left=" + left + " Right=" + right +
                               " Mid=" + mid + " Value=" + arr[mid]);

            if (arr[mid] == target) {
                System.out.println("Found at index " + mid);
                found = true;
                break;
            } else if (arr[mid] < target) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        if (!found) {
            System.out.println("Not Found");
        }

        System.out.println("Total Steps = " + steps);
    }
}
```
## Q3. Bubble Sort Trace
``` java
public class MySelectionSort {
    public static void main(String[] args) {
        int[] arr = {52, 18, 37, 9, 64};

        System.out.print("Before Sorting: ");
        printArray(arr);

        selectionSort(arr);

        System.out.print("After Sorting: ");
        printArray(arr);
    }

    static void printArray(int[] arr) {
        for (int val : arr) {
            System.out.print(val + " ");
        }
        System.out.println();
    }

    static void selectionSort(int[] arr) {
        int n = arr.length;
        int swapCount = 0;

        for (int pass = 0; pass < n - 1; pass++) {
            int minIndex = pass;
            System.out.println("\n--- Pass " + (pass + 1) + " ---");
            System.out.println("Assumed minimum: " + arr[minIndex] + " at index " + minIndex);

            for (int j = pass + 1; j < n; j++) {
                if (arr[j] < arr[minIndex]) {
                    minIndex = j;
                    System.out.println("New minimum found: " + arr[minIndex] + " at index " + minIndex);
                }
            }

            if (minIndex != pass) {
                int temp = arr[pass];
                arr[pass] = arr[minIndex];
                arr[minIndex] = temp;
                swapCount++;
                System.out.println("Swapped: " + arr[pass] + " to index " + pass);
            } else {
                System.out.println("No swap needed!");
            }

            System.out.print("Array after Pass " + (pass + 1) + ": ");
            printArray(arr);
        }

        System.out.println("\nTotal Swaps: " + swapCount);
    }
}
```
