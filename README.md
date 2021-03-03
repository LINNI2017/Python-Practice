# Python-Practice

# Week 33 [4/12-4/18]

# [674](https://leetcode.com/problems/longest-continuous-increasing-subsequence/)
```python
def main(nums):
   cnt = 0
   maxi = 0
   for i in range(len(nums)):
      if nums[i] > nums[i-1]:
            cnt += 1
      else:
            maxi = max(maxi, cnt)
            cnt = 1
   return max(maxi, cnt)
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(N), space = O(1)

# [1331](https://leetcode.com/problems/rank-transform-of-an-array/)
```python
def main(arr):
   book = {}
   arr2 = sorted(arr)
   cnt = 1
   for idx, val in enumerate(arr2):
      if val not in book:
            book[val] = cnt
            cnt += 1
   for idx, val in enumerate(arr):
      arr2[idx] = book[val]
   return arr2
```
#### Assumption: N = the number of elements in the given list
#### Complexity: runtime = O(NlogN) dominant sort cost, space = O(1) exluding result

# [246](https://leetcode.com/problems/strobogrammatic-number/)
```python
def main(num):
   book = {
      '6': '9',
      '9': '6',
      '8': '8',
      '1': '1',
      '0': '0'
   }
   res = ""
   for i in num[::-1]:
      if i in book:
         res += book[i]
      else:
         return False
   return res == num
```
#### Assumption: N = the length of the given num
#### Complexity: runtime = O(N), space = O(1)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)