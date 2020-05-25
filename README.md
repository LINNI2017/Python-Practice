# Python-Practice
## Week 3 [5.18-5.24]
- [719](https://leetcode.com/problems/find-k-th-smallest-pair-distance/)
  - brute force
    - use itertools.combinations
    - O(N^2) `TLE`
  - binary search + slide window
    - sort
    - L=0, R=nums[-1]-nums[0], M=(L+R)//2
      - cnt(paris diff <= M) >= k: R=M
      - else: L=M+1
    - find cnt
      - loop though nums
      - while val-valL>M: L++
      - cnt+=R-L
    - O(NlogN) `AC`
- [4]()
- [410]()
- [540](https://leetcode.com/problems/single-element-in-a-sorted-array/)
  - binary seach
  - L=0, R=len-1, M=(R+L)//2
  - even=(R-M)%2 == 0
  - while L<R loop
    - val[M] == val[M+1]
      - if even: L=M+2 # since M and M+1 are duplicates, right half is even, then exist unique due to M+1
      - else: R=M-1
    - val[M] == val[M-1]
      - if even: R=M-2 # since M and M-1 are duplicates, right half is even, then no unique due to even pairs
      - else: L=M+1
  - O(logN) `AC`
- [148](https://leetcode.com/problems/sort-list/)
  - divide and conquer
  - recursive merge
  - L < R: L.next = merge(L.next, R) return L
  - L >= R: R.next = merge(L, R.next) return R
  - O(NlogN) `AC`
- [775](https://leetcode.com/problems/global-and-local-inversions/)
  - global/local inversion
  - brute force
    - check A[i] > A[j] for i + 1 < j
    - O(N^2) `TLE`
  - memorize minimum
    - mini = min(mini, A[i])
    - traverse array from right to left
    - find global inversion A[i-2] > mini
    - O(N) `AC`
- [5](https://leetcode.com/problems/longest-palindromic-substring/)
  - palindrome s==s[::-1]
  - brute force
    - traverse all permutations of the string
    - for i in range(len(s))
    - for j in range(i+1, len(s)+1)
    - cur = s[i:j]
    - check cur == cur[::-1]
    - O(N^3) `AC`
  - odd/even center check
    - odd length palindrome
      - L, R = i, i
    - even length palindrome
      - L, R = i-1, i
    - L--, R++
    - compare s[L+1:R] with max_str via `R-L-1 and len(max_str)`
    - expand from center (L,R)
    - O(N^2) `AC`
- [153](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)
  - binary search
  - rotated sort
    - 1,2,3,4 L < M < R min is in [L,M]
    - 4,1,2,3 M < R < L min is in [L,M]
    - 3,4,1,2 R < M < L min is in [M,R]
  - L, R = 0, len(nums)-1
  - loop through nums[L] > nums[R]
    - nums[M] < nums[R]: R=M
    - nums[M] >= nums[R]: L=M+1
  - return nums[L]
  - O(logN) `AC`
- [154](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array-ii/)
  - binary search
  - rotated sort with duplicates
  - loop through nums[L] >= nums[R] and L != R
    - nums[M] < nums[R]: R=M
    - nums[M] > nums[R]: L=M+1
    - nums[M] = nums[R]: R--
  - return nums[L]
  - O(logN) `AC`
- [654](https://leetcode.com/problems/maximum-binary-tree/)
  - binary tree
  - recursive build up
  - root of subtree is max of subarray
  - maxi = max(nums[L:R]), maxi_idx = L + nums[L:R].index(maxi)
  - root = TreeNode(maxi)
  - root.left = helper(nums, L, maxi_idx)
  - root.right = helper(nums, maxi_idx+1, R)
  - O(N^2) `AC`  
- [729](https://leetcode.com/problems/my-calendar-i/)
  - brute force
    - store (start, end) in a list
    - search through stored list
    - check existed_start < new_end and new_start < existed_end
    - O(N^2) `AC`
  - binary tree
    - store node(start, end) in a binary tree
      - new_start >= exist_end
        - if not exist.right: exist.right = node
        - else: exist.right.insert(node)
      - new_end <= exist_start
        - if not exist.left: exist.left = node
        - else: exist.left.insert(node)
      - overlap, return False
    - node class
      - keep track of start, end, left, right
    - Worst Case O(N^2), Average Case O(NlogN) `AC`
- [744](https://leetcode.com/problems/find-smallest-letter-greater-than-target/)
  - binary search
  - L=0, R=len(letters), M=(L+R)//2
  - while L < R:
    - target < valM: R=M
    - else: L=M+1
  - L > len(letters) - 1: return letters[0] # wrap around
  - else: return letters[L]
  - O(logN) `AC`
