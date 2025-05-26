# EX 4C DYNAMIC PROGRAMMING – 3
## DATE:
## AIM:
Given a sequence, find the length of the longest palindromic subsequence in it.





## Algorithm
1. Take the input string s for which the longest palindromic subsequence is to be found.
2. Define a recursive function lps(s, i, j) to compute the LPS length between indices i and j.
3. If i > j, return 0 since it's an invalid substring.
4. If i == j, return 1 because a single character is a palindrome of length 1.
5. If s[i] == s[j], return 2 + lps(s, i + 1, j - 1) as matching ends extend the palindrome.
6. If s[i] != s[j], return the maximum of lps(s, i + 1, j) and lps(s, i, j - 1) to explore other subsequences. 

## Program:
```
Program to implement to find the length of the longest palindromic subsequence in it
Developed by: Vinush CV
Register Number: 212222230176
```

```py
def lps(s, i, j):
    if i > j:
        return 0
    if i == j:
        return 1
    if s[i] == s[j]:
        return 2 + lps(s, i + 1, j - 1)
    else:
        return max(lps(s, i + 1, j), lps(s, i, j - 1))

s = input()
print("The length of the LPS is", lps(s, 0, len(s) - 1))


```

## Output:
![image](https://github.com/user-attachments/assets/4ecb6ca0-1dc4-4d23-9541-5128d3d24b51)



## Result:
Thus the program was executed successfully for finding the length of longest palindromic string.
