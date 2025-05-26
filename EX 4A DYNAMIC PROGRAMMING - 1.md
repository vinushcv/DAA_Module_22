# EX 4A DYNAMIC PROGRAMMING - 1
## DATE:
## AIM:
To find longest common subsequence using Dynamic Programming.



## Algorithm
1.Create a 2D table dp where dp[i][j] will store the length of the LCS of the first i characters of string X and the first j characters of string Y. 
2.Initialize the first row and first column with 0.
3.Traverse the strings X and Y:
   If X[i-1] == Y[j-1], then dp[i][j] = dp[i-1][j-1] + 1 (i.e., extend the subsequence by 1).
   Otherwise, dp[i][j] = max(dp[i-1][j], dp[i][j-1]) (i.e., take the longer subsequence without including the current character of X or Y).
4.After filling the table, backtrack from dp[m][n] to construct the LCS string by comparing characters and moving diagonally when they match.
5.The result is stored in the last cell of the table, dp[m][n], representing the length of the LCS.  

## Program:
```
Program to implement the longest common subsequence using Dynamic Programming
Developed by: Vinush CV
Register Number: 212222230176
```
```py
def lcs(X, Y):
    m = len(X)
    n = len(Y)
    
    # Create a 2D array to store lengths of LCS
    dp = [[0] * (n + 1) for _ in range(m + 1)]

    # Build the dp table in bottom-up fashion
    for i in range(m):
        for j in range(n):
            if X[i] == Y[j]:
                dp[i+1][j+1] = dp[i][j] + 1
            else:
                dp[i+1][j+1] = max(dp[i+1][j], dp[i][j+1])

    # Reconstruct LCS from the table
    lcs_result = []
    i, j = m, n
    while i > 0 and j > 0:
        if X[i-1] == Y[j-1]:
            lcs_result.append(X[i-1])
            i -= 1
            j -= 1
        elif dp[i-1][j] > dp[i][j-1]:
            i -= 1
        else:
            j -= 1

    # The LCS is constructed backwards
    return ''.join(reversed(lcs_result))

# Example usage
X = input()
Y = input()
result = lcs(X, Y)
print(result)

```

## Output:
![image](https://github.com/user-attachments/assets/4a9453e1-949f-4547-9303-240894a7d0a4)



## Result:
Thus the program was executed successfully for computing the length of longest common subsequence.
