# EX 4B DYNAMIC PROGRAMMING – 2
## DATE:
## AIM:
To find the longest string (or strings) that is a substring (or are substrings) of two strings..



## Algorithm
1.Create a 2D table lookup of size (m+1) x (n+1), where m and n are the lengths of strings X and Y, respectively.
2.Initialize maxLength as 0 and endingIndex as m to store the end index of the longest common substring.
3.Loop through each character of both strings (X[i-1] and Y[j-1]):
4.If the characters match, update lookup[i][j] = lookup[i-1][j-1] + 1.
5.If the characters don't match, set lookup[i][j] = 0.
6.Track the maximum length found and update maxLength and endingIndex accordingly.
7.The longest common substring is the substring of X that starts from endingIndex - maxLength and ends at endingIndex.


## Program:
```
Program to implement the longest common substring problem
Developed by: Vinush CV
Register Number: 212222230176
```
```py
def lcs(X, Y):
    m = len(X)
    n = len(Y)
    
    # Create a 2D DP array with 0s
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    
    max_length = 0  # To store the length of the longest common substring
    end_pos = 0  # To store the ending position of the longest common substring in X

    # Fill the DP table
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if X[i - 1] == Y[j - 1]:
                dp[i][j] = dp[i - 1][j - 1] + 1
                if dp[i][j] > max_length:
                    max_length = dp[i][j]
                    end_pos = i  # Update the ending position of the substring
            else:
                dp[i][j] = 0

    # The longest common substring is X[end_pos - max_length : end_pos]
    return X[end_pos - max_length : end_pos], max_length

# Example usage:
X = input()
Y = input()
substring, length = lcs(X, Y)
print(f"The longest common substring is {substring}")

```

## Output:
![image](https://github.com/user-attachments/assets/6ca1b91a-8095-4c26-8555-181a9f4f99f2)



## Result:
Thus the program was executed successfully for finding the longest common substring .
