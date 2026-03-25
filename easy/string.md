# 🔤 String - Easy 題型整理

---

## 125. Valid Palindrome (迴文判斷)
* **核心技巧**: `Regular Expression` (正則表達式)、`Two Pointers`
* **時間複雜度**: $O(n)$

**解題思路與關鍵問題：**
使用雙指標從頭尾同時向中間移動並比對。為了讓邏輯簡潔，先用 `re.sub` 清洗字串，將非字母數字的字元剔除並轉為小寫。

**Python 實作：**
```python
import re
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s = re.sub("[^a-zA-Z0-9]", "", s).lower()
        start = 0
        end = len(s) - 1

        while start <= end:
            if s[start] != s[end]:
                return False
            start += 1
            end -= 1
        return True