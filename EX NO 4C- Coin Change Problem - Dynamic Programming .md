
# EX 4C Coin Change Problem - Dynamic Programming.
## DATE:16-03-2026

## AIM:

To write a Java program to for given constraints.
You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.

Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

You may assume that you have an infinite number of each kind of coin.

## Algorithm:

1. Read the coin denominations array and the target amount.
2. Create a DP array `dp[]` of size `amount + 1`, filled with a large value (amount + 1).
3. Set `dp[0] = 0` because 0 coins are needed to make amount 0.
4. For each amount `i` from 1 to `amount`, check each coin:

   * If `coin <= i`, update
     `dp[i] = min(dp[i], dp[i - coin] + 1)`
5. After filling the DP table:

   * If `dp[amount]` is still greater than amount, return **-1**.
   * Else return `dp[amount]`.
6. Print the result.

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

public class Solution {
    public int coinChange(int[] coins, int amount) {
        //ADD YOUR CODE HERE
        int max = amount+1;
        int[] dp=new int[max];
        Arrays.fill(dp,max);
        dp[0]=0;
        
        for(int i=1;i<=amount;i++)
        {
            for(int coin:coins)
            {
                if(coin<=i)
                {
                    dp[i]=Math.min(dp[i],dp[i-coin]+1);
                }
            }
        }
        
        return dp[amount]>amount ? -1:dp[amount];
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Solution solution = new Solution();
        String coinsLine = scanner.nextLine(); 
        String amountLine = scanner.nextLine();
        coinsLine = coinsLine.replaceAll("[^0-9,]", ""); 
        String[] coinsStr = coinsLine.split(",");
        int[] coins = new int[coinsStr.length];
        for (int i = 0; i < coinsStr.length; i++) {
            coins[i] = Integer.parseInt(coinsStr[i]);
        }
        int amount = Integer.parseInt(amountLine.replaceAll("[^0-9]", ""));
        int result = solution.coinChange(coins, amount);
        System.out.println(result);

        scanner.close();
    }
}

```
## Output:

<img width="360" height="247" alt="image" src="https://github.com/user-attachments/assets/9c2eb466-5d56-4039-97f6-7d81d10a632e" />


## Result:
The program successfully implemented and the expected output is verified.
