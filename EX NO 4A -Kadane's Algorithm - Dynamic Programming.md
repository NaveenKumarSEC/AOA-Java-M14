
# EX 4A Kadane's Algorithm - Dynamic Programming. 
## DATE:16-03-2026

## AIM:

To Write a Java program to solve the below problem using Kadane's Algorithm.
A solar company installs solar panels around a circular grid of n buildings. Each building either generates or consumes net energy, represented by integers (+ve for generated, -ve for consumed).

The company wants to find a contiguous sequence of buildings (possibly wrapping around from the end to the beginning) that maximizes the total net energy.

Write a program to compute the maximum net energy that can be collected from any contiguous block of buildings on the circular grid.

Input Format:
First line: Integer n (number of buildings)

Second line: n space-separated integers: net energy for each building

Output Format:
A single integer: Maximum net energy collectable from a contiguous block (wrapping allowed)

Constraints:
1 <= n <= 10^6

## Algorithm:

1. Read the number of buildings `n` and the net energy values.
2. Use **Kadane’s Algorithm** to find the maximum subarray sum (non-circular case).
3. Use **Kadane’s Algorithm (inverted)** to find the minimum subarray sum.
4. Compute the total sum of all energy values.
5. If all values are negative, return the maximum value directly.
6. Otherwise, compute the maximum circular sum as
   `totalSum - minSum`.
7. The answer is the maximum of:

   * Normal maximum subarray sum
   * Circular maximum subarray sum
8. Print the result.  

## Program:
```
/*
Program to implement Reverse a String
Developed by: Naveenkumar M
Register Number:  212224230182
*/
```
```
import java.util.*;
public class SolarEnergyMaximizer {
    public static int maxCircularEnergy(int[] energy) {
        int n = energy.length;
        if (n == 1) return energy[0];
        int maxSum = kadaneMax(energy);
        int totalSum = 0;
        for (int i = 0; i < n; i++) {
            totalSum += energy[i];
            energy[i] = -energy[i];
        }
        int minSum = kadaneMax(energy);
        for (int i = 0; i < n; i++) {
            energy[i] = -energy[i];
        }
        int circularMax = totalSum + minSum;
        if (circularMax == 0) return maxSum;
        return Math.max(maxSum, circularMax);
    }
    public static int kadaneMax(int[] arr) {
        int maxSoFar = arr[0];
        int maxEndingHere = arr[0];
        for (int i = 1; i < arr.length; i++) {
            maxEndingHere = Math.max(arr[i], maxEndingHere + arr[i]);
            maxSoFar = Math.max(maxSoFar, maxEndingHere);
        }
        return maxSoFar;
    }
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int[] energy = new int[n];
        for (int i = 0; i < n; i++) {
            energy[i] = sc.nextInt();
        }
        System.out.println(maxCircularEnergy(energy));
    }
}
```
## Output:

<img width="487" height="245" alt="image" src="https://github.com/user-attachments/assets/aa8d0804-d4bf-4ea4-88ef-3a97d168250d" />


## Result:
The program successfully Implemented and the output is verified. 
