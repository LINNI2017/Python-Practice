# Python-Practice

# Week 63 [11/8-11/14]
# [114](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/)
```python
def main(root):
   dfs(root, [None])

def dfs(root, pre):
   if not root: return
   dfs(root.right, pre)
   dfs(root.left, pre)
   root.right, pre[0] = pre[0], root
   root.left = None
```
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N), space = O(N) recursive call stack

# [285](https://leetcode.com/problems/inorder-successor-in-bst/)
```python
def main(root, p):
   pre = [None]
   dfs(root, p, pre)
   return pre[0]

def dfs(root, p, pre):
   if not root: return
   if p.val >= root.val:
      dfs(root.right, p, pre)
   else:
      pre[0] = root
      dfs(root.left, p, pre)
```
#### Note: Utilize DFS recursion
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N), space = O(N) recursive call stack
```python
def main(root, p):
   res = None
   while root:
      if p.val >= root.val:
         root = root.right
      else:
         res = root
         root = root.left
   return res
```
#### Note: Utilize DFS iteration, the trick is to maintain parent before moving to smaller left children, and move to right children if current node is too small
#### Assumption: N = the number of nodes in the tree
#### Complexity: runtime = O(N), space = O(N) recursive call stack

# [1261](https://leetcode.com/problems/find-elements-in-a-contaminated-binary-tree/)
```python
class FindElements:
   def __init__(self, root):
      self.found = set()
      if root.val == -1:
         root.val = 0
      self.dfs(root)
   
   def dfs(self, root):
      if not root:
         return
      self.found.add(root.val)
      base = root.val * 2 + 1
      if root.left:
         root.left.val = base
         self.dfs(root.left)
      if root.right:
         root.right.val = base + 1
         self.dfs(root.right)

   def find(self, target):
      return target in self.found
```
#### Assumption: N = the number of elements
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
