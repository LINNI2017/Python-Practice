# Python-Practice

# Week 57 [9/27-10/3]

# [1796](https://leetcode.com/problems/second-largest-digit-in-a-string/)
```python
def main(s):
   maxi = [-1, -1]
   for i in s:
      if i.isnumeric():
         cur = int(i)
         if cur > maxi[0]:
            maxi[0], maxi[1] = cur, maxi[0]
         elif cur != maxi[0] and cur > maxi[1]:
            maxi[1] = cur
   return maxi[1]
```
#### Assumption: N = the length of the given string
#### Complexity: runtime = O(N), space = O(1)

# [1543](https://leetcode.com/problems/fix-product-name-format/)
```sql
SELECT LOWER(TRIM(product_name)) AS PRODUCT_NAME,
       DATE_FORMAT(sale_date, "%Y-%m") AS SALE_DATE,
       COUNT(*) AS TOTAL
FROM Sales
WHERE sale_date BETWEEN "2000-01-01" AND "2000-12-30"
GROUP BY LOWER(TRIM(product_name)), DATE_FORMAT(sale_date, "%Y-%m")
ORDER BY PRODUCT_NAME ASC, SALE_DATE ASC
```
```sql
SELECT LOWER(TRIM(product_name)) AS PRODUCT_NAME,
       DATE_FORMAT(sale_date, "%Y-%m") AS SALE_DATE,
       COUNT(*) AS TOTAL
FROM Sales
WHERE YEAR(sale_date) = 2000
GROUP BY LOWER(TRIM(product_name)), DATE_FORMAT(sale_date, "%Y-%m")
ORDER BY PRODUCT_NAME ASC, SALE_DATE ASC
```
```sql
SELECT LOWER(TRIM(product_name)) AS PRODUCT_NAME,
       DATE_FORMAT(sale_date, "%Y-%m") AS SALE_DATE,
       COUNT(*) AS TOTAL
FROM Sales
WHERE YEAR(sale_date) = 2000
GROUP BY LOWER(TRIM(product_name)), MONTH(sale_date)
ORDER BY PRODUCT_NAME ASC, SALE_DATE ASC
```

# [1812](https://leetcode.com/problems/determine-color-of-a-chessboard-square/)
```python
def main(coordinates):
   return (ord(coordinates[0]) - 96 + int(coordinates[1])) % 2 == 1
```
#### Note: the sum of coordinates is even if black, otherwise odd white
#### Assumption: N = the size of coordinate
#### Complexity: runtime = O(1), space = O(1)

# [1893](https://leetcode.com/problems/check-if-all-the-integers-in-a-range-are-covered/)
```python
def main(ranges, left, right):
   cur = set(range(left, right+1))
   for start, end in ranges:
      for i in range(start, end+1):
         if i in cur:
            cur.remove(i)
   return not cur
```
#### Assumption: N = the number of elements between left and right
#### Complexity: runtime = O(N), space = O(N)

# [1897](https://leetcode.com/problems/redistribute-characters-to-make-all-strings-equal/)
```python
from collections import defaultdict as dd
def main(words):
   book = dd(int)
   size = len(words)
   for word in words:
      for i in word:
         book[i] += 1
   for i in book:
      if book[i] % size != 0:
         return False
   return True
```
#### Assumption: N = the number of words
#### Complexity: runtime = O(N), space = O(N)

### Template
# []()
```sql
```

# []()
```python
```
#### Assumption: N = ??
#### Complexity: runtime = O(?), space = O(?)
