# 🥞 Stack - Easy 題型整理

這份文件收錄了有關於堆疊（先進後出 LIFO）的基礎題型。

---

## 20. Valid Parentheses (有效的括號)
* **核心技巧**: `Stack` (使用 Python `list` 模擬)
* **時間複雜度**: $O(n)$

**解題思路與關鍵問題：**
利用 Stack 來記錄「還沒被關閉的左括號」。遇到左括號就放進去，遇到右括號就從 Stack 拿出最後一個左括號來比對。

**Q：`if not stack:` 代表什麼意思？**
在 Python 中，空的串列在布林邏輯下為 `False`。`not stack` 代表「堆疊是空的」。
如果遇到右括號但 Stack 是空的，代表「沒有對應的左括號可以關閉」，直接回傳 `False`。最後回傳 `not stack` 則是為了確保所有左括號都被成功抵銷。

**Python 實作：**
```python
class Solution:
    def isValid(self, s: str) -> bool:
        mapping = {")": "(", "]": "[", "}": "{"}
        stack = []

        for char in s:
            if char in mapping.values():
                stack.append(char)
            elif char in mapping:
                if not stack or mapping[char] != stack.pop():
                    return False
        return not stack