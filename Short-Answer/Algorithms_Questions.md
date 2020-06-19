# Analysis of Algorithms

## Exercise I

Give an analysis of the running time of each snippet of
pseudocode with respect to the input size n of each of the following:

```python
a)  a = 0                    
    while (a < n * n * n):   
      a = a + n * n
```

O(n^3) (number of times the while loop executes is the cube of n)


```
b)  sum = 0                 (1)
    for i in range(n):      (n)
      j = 1                 (1)
      while j < n:          (n)
        j *= 2              (1)
        sum += 1            (1)
```

O(n^2)

outer loop occurs n times
inner loop occurs (up to) n times


```
c)  def bunnyEars(bunnies):
      if bunnies == 0:
        return 0

      return 2 + bunnyEars(bunnies-1)

O(n)

Say n = 1000:
test for b == 0 takes one 'step'
recursion involves one (__only one__) recursive call, with n varying liearly
    
```

## Exercise II

Suppose that you have an n-story building and plenty of eggs. Suppose also that an egg gets broken if it is thrown off floor f or higher, and doesn't get broken if dropped off a floor less than floor f. Devise a strategy to determine the value of f such that the number of dropped + broken eggs is minimized.

Write out your proposed algorithm in plain English or pseudocode AND give the runtime complexity of your solution.

Plain English:

Big picture, this is a binary search, and can be addressed recursively.


O(logn)


Edge case: n == 0 : return 'No building'

Recursion strategy:

tracking variables:
max_safe_so_far (starts at 0)
low (starts at 1)
high (starts at n)
current_floor (will start at n // 2 + 1)

Test halfway up (n //2 + 1) 

If it does not break, reset safest floor as current tested floor, and, if low != high recurse, from current floor + to highest

If it does break, DO NOT reset max_safe_so_far, and, if low != high, recurse from low to current.

I'd do detailed testingon lists of size 1, 2, 3, 4, 100