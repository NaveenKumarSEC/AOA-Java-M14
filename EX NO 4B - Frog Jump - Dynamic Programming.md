
# EX 4B Frog Jump - Dynamic Programming.
## DATE:16-03-2026

## AIM:

To write a Java program to for given constraints.
A Frog Jump 1 or 2 steps at a time.
Problem Statement:

A frog is at the bottom of the stairs with n steps. It can jump either 1 or 2 steps at a time. Write a program to find the number of distinct ways the frog can reach the top (n-th step).

Input Format:

A single integer n (1 ≤ n ≤ 45) – number of steps.
 Output Format:

A single integer – number of distinct ways to reach step n.

## Algorithm:

1. Read the value of `n` (number of steps).
2. If `n` is 0 or 1, return 1 (only one way).
3. Create an array `dp[]` of size `n + 1`.
4. Initialise `dp[0] = 1` and `dp[1] = 1`.
5. For each step from 2 to n, compute:
   `dp[i] = dp[i − 1] + dp[i − 2]`
6. The final answer is stored in `dp[n]`.
7. Print the result.    

## Program:
```
/*
Program to implement Reverse a String
Developed by: Naveenkumar M
Register Number:  212224230182
*/
```
```
import java.util.Scanner;

public class FrogJump {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
       
        int n = scanner.nextInt();
        scanner.close();

        System.out.println(countWays(n));
    }

   
public static long countWays(int n) {       //Type your code here
       if(n==1) return 1;
if(n==2) return 2;
long[] dp = new long[n+1];
dp[1] = 1;
dp[2] = 2;
for(int i=3; i<=n; i++) {
dp[i] = dp[i-1] + dp[i-2];
}
return (long)dp[n];       
    }
}

```

## Output:

<img width="441" height="212" alt="image" src="https://github.com/user-attachments/assets/ebad1618-c366-4933-832f-98ac57d2b4c7" />


## Result:
The program successfully implemented and the expected output is verified.
