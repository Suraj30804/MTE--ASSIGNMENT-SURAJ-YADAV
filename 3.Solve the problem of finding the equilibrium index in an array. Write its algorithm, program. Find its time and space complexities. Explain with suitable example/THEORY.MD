
Sure! Below are the Java implementations for each of the problems along with explanations, algorithms, time and space complexities, and suitable examples.
### **3. Finding the Equilibrium Index in an Array**
**Algorithm:**

1. Calculate the total sum of the array.
1. Initialize a variable leftSum to 0.
1. Iterate through the array:
   1. For each index i, check if leftSum is equal to totalSum - leftSum - arr[i].
   1. If they are equal, return the index i.
   1. Update leftSum by adding arr[i] to it.
1. If no equilibrium index is found, return -1.

**Java Program:**

public class EquilibriumIndex {
`    `public static int findEquilibriumIndex(int[] arr) {
`        `int totalSum = 0;
`        `for (int num : arr) {
`            `totalSum += num;
`        `}

`        `int leftSum = 0;
`        `for (int i = 0; i < arr.length; i++) {
`            `if (leftSum == totalSum - leftSum - arr[i]) {
`                `return i;
`            `}
`            `leftSum += arr[i];
`        `}

`        `return -1; // No equilibrium index found
`    `}

`    `public static void main(String[] args) {
`        `int[] arr = {1, 3, 5, 2, 2};
`        `System.out.println(findEquilibriumIndex(arr)); // Output: 2
`    `}
}


**Time Complexity:** O(n)

**Space Complexity:** O(1) 

**Explanation:** In the example, the equilibrium index is 2 because the sum of elements on the left (1 + 3) equals the sum of elements on the right (2 + 2).

### **4. Check if an Array Can Be Split into Two Parts with Equal Sums**
**Algorithm:**

1. Calculate the total sum of the array.
1. If the total sum is odd, return false (it can't be split evenly).
1. Initialize a variable leftSum to 0.
1. Iterate through the array:
   1. Add each element to leftSum.
   1. If leftSum equals totalSum / 2, return true.
1. If no such split is found, return false.

**Java Program:**

public class SplitArray {
`    `public static boolean canSplitArray(int[] arr) {
`        `int totalSum = 0;
`        `for (int num : arr) {
`            `totalSum += num;
`        `}

`        `if (totalSum % 2 != 0) {
`            `return false; // Cannot split evenly
`        `}

`        `int leftSum = 0;
`        `for (int num : arr) {
`            `leftSum += num;
`            `if (leftSum == totalSum / 2) {
`                `return true;
`            `}
`        `}

`        `return false; // No valid split found
`    `}

`    `public static void main(String[] args) {
`        `int[] arr = {1, 2, 3, 3};
`        `System.out.println(canSplitArray(arr)); // Output: true
`    `}
}


**Time Complexity:** O(n)

**Space Complexity:** O(1) 

**Explanation:** In the example, the array can be split into two parts: [1, 2] and [3, 3], both summing to 3.

### **5. Maximum Sum of Any Subarray of Size K**
**Algorithm:**

1. Initialize a variable maxSum to 0 and calculate the sum of the first K elements.
1. Set maxSum to this initial sum.
1. Slide the window across the array:
   1. For each new element, subtract the element that is sliding out of the window and add the new element.
   1. Update maxSum if the new sum is greater.
1. Return maxSum.

**Java Program:**

\```java public class MaxSumSubarray { public static int maxSumSubarray(int[] arr, int k) { int n = arr.length; if (n < k) { return -1; // Not enough elements }

`   `int maxSum = 0;
`    `for (int i = 0; i < k; i++) {
`        `maxSum += arr[i];
`    `}

`    `int windowSum = maxSum;
`    `for (int i = k; i < n; i++) {
`        `windowSum += arr[i] - arr[i - k];
`        `maxSum = Math.max(maxSum, windowSum);
`    `}

`    `return maxSum;
}

public static void main(String[] args) {
`    `int[] arr = {2, 1, 5, 1, 3, 2};
`    `int k = 3;
`    `System.out.println
