```
from itertools import permutations

def check_permutations_divisible_by_7(string):
    digits = list(string)
    perms = permutations(digits)
    divisible_permutations = []

    for perm in perms:
        num = int(''.join(perm))
        if num % 7 == 0:
            divisible_permutations.append(num)

    if divisible_permutations:
        smallest = min(divisible_permutations)
        largest = max(divisible_permutations)
        average = (smallest + largest) / 2
        return average
    else:
        return None

integer_string = "1867"
average = check_permutations_divisible_by_7(integer_string)

if average is not None:
    print("The average between the smallest and largest permutation divisible by 7 is:", average)
else:
    print("No permutation of the digits in", integer_string, "is divisible by 7.")
```

## Output
```The average between the smallest and largest permutation divisible by 7 is: 5152.0```




