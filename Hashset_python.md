# Hash Set Implementation in Python

```python
class HashSet:
    def __init__(self):
        self.hash_set = {}

    def add(self, key):
        self.hash_set[key] = True

    def remove(self, key):
        if key in self.hash_set:
            del self.hash_set[key]

    def search(self, key):
        return key in self.hash_set

    def get_elements(self):
        return list(self.hash_set.keys())

# Example usage:

obj = HashSet()

obj.add(1)
obj.add(2)
obj.add(3)

# Search for an element
key = 2
print(f"Set contains {key}: {obj.search(key)}") # Returns true

# Display all elements
print("Elements in the set:", obj.get_elements()) # displays : [1, 2, 3]

```

`Output`

```
True

[1, 2, 3]
```

# Sum Of Pairs 
### Solution using Hash Set


Given an array of integers and a number K, check if there exist a pair of indices i,j s.t. a[i] + a[j] = K and i!=j.

```
Input Format

The first line of input contains T - the number of test cases. It's followed by 2T lines, first line of each test case contains N - the size of the array and K, and the next line contains N space separated integers - the elements of the array.

```

```
Output Format

For each test case, print "True" if such a pair exists, "False" otherwise, separated by newline.

```

Constraints

30 points

1 <= T <= 100

2 <= N <= 1000



70 points

1 <= T <= 300

2 <= N <= 10000



General Constraints

-108 <= K <= 108

-108 <= ar[i] <= 108



Example :
```

Input

3

5 -15

-30 15 20 10 -10

2 20

10 10

4 7

-4 0 10 -7



Output

True

True

False
```

```code```

```python
class Hashset:
    def __init__(self):
        self.s = {}

    def insert(self, k):
        self.s[k]=True

    def search(self, k):
        return k in self.s
        
for _ in range(int(input())):
    obj = Hashset()
    N, K = map(int, input().split())
    arr = list(map(int, input().split()))
    flag = False
    for i in range(len(arr)):
        if obj.search(K-arr[i])==True:
            flag = True
            break
        else:
            obj.insert(arr[i])
    if flag:
        print("True")
    else:
        print("False")
```


