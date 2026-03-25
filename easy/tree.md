

# 🌳 Tree - Easy 題型整理

這份文件收錄了有關於二元樹的基礎題型，重點在於理解遞迴與疊代走訪。

---

## 226. Invert Binary Tree (翻轉二元樹)
* **核心技巧**: `Recursion` (遞迴)、`BFS` (廣度優先)
* **時間複雜度**: $O(n)$


**解題思路：**
遞迴的底層思維是將大問題拆解為「左子樹翻轉」與「右子樹翻轉」，最後將左右子節點互換。這就像是每到一個節點，就把它下面的兩個子節點換位置。

**Python 實作 (疊代 BFS 版)：**
```python
from collections import deque
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root:
            return root
        queue = deque([root])

        while queue:
            current = queue.popleft()
            current.right, current.left = current.left, current.right

            if current.left:
                queue.append(current.left)
            if current.right:
                queue.append(current.right)
        return root
```
**Python 實作 (遞迴)：**
```python
    def invertTree(self, root: Optional[TreeNode]) -> Optionl[TreeNode]:
        if not root:
            return root

        self.invertTree(root.left)
        self.invertTree(root.right)

        root.left,root.right = root.right, root.left
        
        return root
```
