## Code
```
def findMinimumDeletion(x, z, dp, y):
    if x > z:
        return 0
    if x == z:
        return 1
    if dp[x][z] != -1:
        return dp[x][z]

    res = 1 + findMinimumDeletion(x + 1, z, dp, y)

    for i in range(x + 1, z + 1):
        if y[x] == y[i]:
            res = min(
                res,
                findMinimumDeletion(x + 1, i - 1, dp, y) +
                findMinimumDeletion(i, z, dp, y)
            )

    dp[x][z] = res
    return res


if __name__ == "__main__":
    y = "kjslaqpwoereeeeewwwefifjdksjdfhjdksdjfkdfdlddkjdjfjfjfjjjjfjffnefhkjgefkgjefkjgkefjekihutrieruhigtefhgbjkkkknbmssdsdsfdvneurghiueor"
    n = len(y)
    dp = [[-1 for _ in range(n)] for _ in range(n)]
    print(findMinimumDeletion(0, n - 1, dp, y))
```

## Output
```
78
```





