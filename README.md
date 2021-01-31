# Python-Practice

# Week 25 [2/15-2/21]

# [498](https://leetcode.com/problems/diagonal-traverse/)
```python
from collections import defaultdict as dd
def main(matrix):
   if not matrix:
      return matrix
   row_size = len(matrix)
   col_size = len(matrix)
   res = dd(list)
   ans = []
   for i in range(row_size):
      for j in range(col_size):
         k = i + j
         if k % 2 == 0:
            res[k] = [matrix[i][j]] + res[k]
         else:
            res[k] += [matrix[i][j]]
   for i in res:
      ans += res[i]
   return ans
```
#### Assumption: M = the number of rows in the given matrix, N = the number of cols in the given matrix
#### Complexity: runtime = O(MN), space = O(MN)

# [941](https://leetcode.com/problems/valid-mountain-array/)
```python
def main(arr):
   size = len(arr)
   if size < 3:
      return False
   idx = 1
   while idx < size and arr[idx] > arr[idx-1]:
      idx += 1
   if idx == 1 or idx == size:
      return False
   while idx < size and arr[idx] > arr[idx-1]:
      idx += 1
   return idx == size and arr[idx-1] < arr[idx-2]
```
#### Assumption: N = the number of elements in the given
#### Complexity: runtime = O(N), space = O(1)

# [59](https://leetcode.com/problems/spiral-matrix-ii/)
```python
def main(n):
   DIRS = [(0,1),(1,0),(0,-1),(-1,0)]
   # -> | <- ^
   #    v    |
   cur = 0
   res = [[0] * n for _ in range(n)]
   x, y = 0, 0
   for i in range(1, n**2+1):
      res[x][y] = i
      dx, dy = DIRS[cur % 4]
      if 0<=x+dx<n and 0<=y+dy<n and not res[x+dx][y+dy]:
            pass
      else:
            cur += 1
            dx, dy = DIRS[cur % 4]
      x += dx
      y += dy
   return res
```
#### Assumption: N = the matrix length size
#### Complexity: runtime = O(N*N), space = O(1)

# [453](https://leetcode.com/problems/minimum-moves-to-equal-array-elements/)
```python
def main(nums):
   return sum(nums) - min(nums) * len(nums)
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [703](https://leetcode.com/problems/kth-largest-element-in-a-stream/)
```python
from heapq import heappush, heappushpop
class KthLargest:
   def __init__(self, k, nums):
      self.k = k
      self.nums = nums
      for i in nums:
         if len(self.nums) < k:
            heappush(self.nums, i)
         else:
            if i > self.nums[0]:
               heappushpop(self.nums, i)
   
   def add(self, val):
      if len(self.nums) < self.k:
         heappush(self.nums, val)
      else:
         if val > self.nums[0]:
            heappushpop(self.nums, val)
      return self.nums[0]
```
#### Assumption: N = the number of elements in nums, K = the rank of largest num to request
#### Complexity: init runtime = O(NlogK), add runtime = O(logK), space = O(1)

# [724](https://leetcode.com/problems/find-pivot-index/)
```python
def main(nums):
   if not nums:
      return -1
   l = 0
   r = sum(nums) - nums[0]
   if l == r:
      return 0
   for i in range(1, len(nums)):
      l += nums[i-1]
      r -= nums[i]
      if l == r:
            return i
   return -1
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(1)

# [238](https://leetcode.com/problems/product-of-array-except-self/)
```python
def main(nums):
   res = [1]
   cur = 1
   for idx in range(1, len(nums)):
      cur *= nums[idx-1]
      res += [cur]
   cur = 1
   for idx in range(1, len(nums)+1):
      res[-idx] *= cur
      cur *= nums[-idx]
   return res
```
#### Assumption: N = the number of elements
#### Complexity: runtime = O(N), space = O(1)

# [263](https://leetcode.com/problems/ugly-number/)
```python
def main(num):
   if num == 0:
      return False
   while num % 2 == 0:
      num //= 2
   while num % 3 == 0:
      num //= 3
   while num % 5 == 0:
      num //= 5
   return num == 1
```
#### Assumption: the given number = 2^A * 3^B * 5^C
#### Complexity: runtime = O(A+B+C), space = O(1)

# [172](https://leetcode.com/problems/factorial-trailing-zeroes/)
```python
def main(n):
   cnt = 0
   while n > 0:
      n //= 5
      cnt += n
   return cnt
```
#### Assumption: N = the number size
#### Complexity: runtime = O(logN), space = O(1)

# [1399](https://leetcode.com/problems/count-largest-group/)
```python
from collections import defaultdict as dd
def main(n):
   book = dd(int)
   maxi, cnt = 0, 0
   for i in range(1, n+1):
      cur = 0
      while i > 0:
         cur += i % 10
         i //= 10
      book[cur] += 1
      if book[cur] > maxi:
         maxi = book[cur]
         cnt = 1
      elif book[cur] == maxi:
         cnt += 1
   return cnt
```
#### Assumption: N = the number size
#### Complexity: runtime = O(N), space = O(N)

# [1180](https://leetcode.com/problems/count-substrings-with-only-one-distinct-letter/)
```python
def main(S):
   cnt, cont, pre = 0, 0, None
   for i in S:
      if i != pre:
         cnt += (1 + cont) * cont // 2
         cont = 1
         pre = i
      else:
         cont += 1
   return cnt + (1 + cont) * cont // 2
```
#### Assumption: N = the length of the string S
#### Complexity: runtime = O(N), space = O(1)

# [1175](https://leetcode.com/problems/prime-arrangements/)
```python
from math import sqrt, factorial as f
def is_prime(num):
   for i in range(2, int(sqrt(num)) + 1):
      if num % i == 0:
         return False
   return num > 1

def main(n):
   cnt = 0
   for i in range(1, n+1):
      if is_prime(i):
         cnt += 1
   return f(cnt) * f(n-cnt) % (10 ** 9 + 7)
```
#### Assumption: N = the number size
#### Complexity: runtime = O(N^1.5) = O(N^0.5) from is_prime for loop * O(N) from main for loop, space = O(1)

### Template
# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)