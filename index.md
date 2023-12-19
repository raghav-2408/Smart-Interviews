# Check Anagrams
```python
a = "swot"
b = "twos"
a.sort()
a = ''.join(sorted(a))
b = ''.join(sorted(b))
print(a, b)
```


# Longest Palindromic strings

```python
def func(s, p1, p2):
    while p1>=0 and p2<len(s) and s[p1] == s[p2]:
        p1-=1
        p2+=1
    return p2-p1-1

for _ in range(int(input())):
    N = int(input())
    S = input()
    ans = 1
    for i in range(1, len(S)+1):
        ans = max(ans, func(S, i-1, i)) 
        ans = max(ans, func(S, i-1, i+1)) 
    print(ans)
```

# First Repeating Character - 1

```python
from collections import Counter
for _ in range(int(input())):
    S = input()
    res = Counter(S)
    for k, v in res.items():
        if v>1:
            print(k)
            break
    else:
        print(".")
```

#   First Repeating Character - 2

```python
def c(s, a):
    for i in range(len(s)):
        if s[i] not in a:
            a.append(s[i])
        else:
            return s[i]
    else:
        return '.'
for _ in range(int(input())):
    s = input()
    a = []
    x = c(s, a)
    print(x)
```

# Sum of Pairs
```python
class HS:
    def __init__(self) -> None:
        self.s = []
    def insert(self, ele):
        self.s.append(ele)
        return self.s
        return self.s
    def search(self, ele):
        return ele in self.s

for _ in range(int(input())):
    obj = HS()
    N, K = map(int, input().split())
    a = list(map(int, input().split()))
    flag = False
    for i in range(len(a)):
        if obj.search(K-a[i]) == True:
            flag = True
            break
        else:
            obj.insert(a[i])
    if flag:
        print("True")
    else:
        print("False")
```

# Rearrange Sequence 1

```python
for _ in range(int(input())):
    N = int(input())
    a = list(map(int, input().split()))
    ans = 0
    for i in range(N):
        mn = 10**5+1
        mx = -1
        for j in range(i, N):
            mx = max(mx, a[j])
            mn = min(mn, a[j])
            if mx-mn+1 == j-i+1:
                ans = max(ans, j-i+1)
    print(ans)
```

# Rearrange Sequence 2

```python
for _ in range(int(input())):
    N = int(input())
    a = list(map(int, input().split()))
    ans = 0
    for i in range(N):
        mx = -1
        mn = 10**5+1
        s = set()
        for j in range(i, N):
            mx = max(mx, a[j])
            mn = min(mn, a[j])
            s.add(a[j])
            if mx-mn+1 == len(s):
                ans = max(ans, len(s))
    print(ans)
```

# Finding Frequency

```python
from collections import Counter
N = int(input())
a = list(map(int, input().split()))
res = Counter(a)
Q = int(input())
for i in range(Q):
    X = int(input())
    if X in res:
        print(res[X])
    else:
        print("0")
```

# X 1s and Y 0s


```python
for i in range(int(input())):
    x,y=map(int,input().split())
    print(((1<<x)-1<<y)%1000000007)
```
# X and Y set Bits


```python
for i in range(int(input())):
    x,y=map(int,input().split())
    print(((1<<x)|1<<y)%1000000007)  
```

# Count Set Bits

```python
for i in range(int(input())):
    n=int(input())
    count=0
    while(n>0):
        count+=1
        n=n&(n-1)
    print(count)
```

# Enclosing Substring

```python
def valid(cntA, cntB):
    for i in range(26):
        if cntB[i] > cntA[i]:
            return False 
    return True

def func(A, B):
    cntA = [0]*26
    cntB = [0]*26

    for i in range(len(B)):
        cntB[ord(B[i]) - ord('a')] += 1
    
    i=0
    j=0
    res = float('inf')

    while j<len(A):
        cntA[ord(A[j]) - ord('a')] +=1
        while valid(cntA, cntB):
            res = min(res, j-i+1)
            cntA[ord(A[i]) - ord('a')] -=1
            i+=1
        j+=1
    return res if( res!=float('inf')) else -1

for _ in range(int(input())):
    B, A = map(str, input().split())
    x = func(A, B)
    print(x)

```


# Distinct Elements in Window (partial)


```python
class Hashset:
    def __init__(self):
        self.s = set()
    def insert(self, x):
        self.s.add(x)

def func(arr, k):
    for i in range(len(arr)-k+1):
        obj = Hashset()
        for j in range(i, i+k):
            obj.insert(arr[j])
        print(len(obj.s), end=" ")

for _ in range(int(input())):
    N, K = map(int, input().split())
    arr = list(map(int, input().split()))
    func(arr, K)
    print()
```