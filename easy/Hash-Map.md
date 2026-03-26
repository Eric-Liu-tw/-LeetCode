# 🔑 Hash Map - Easy 題型整理

這份文件收錄了有關於 Hash Map (雜湊表) 的基礎題型，重點在於理解鍵值對的查詢應用與頻率統計。

---

## 242. Valid Anagram (有效的字母異位詞)
* **核心技巧**: `Hash Table` (雜湊表)、`Frequency Counter` (頻率統計)
* **時間複雜度**: $O(n)$，其中 $n$ 為字串長度。
* **空間複雜度**: $O(1)$ (因為英文字母最多 26 個，無論字串多長，Hash Map 最多只會存 26 組鍵值對，所需空間為常數)

**解題思路：**
這題的核心在於「頻率統計」。字母異位詞的意思是兩個字串包含的字元種類與數量完全相同，只是排列順序不同。最直觀的做法是：先確認兩個字串長度是否相等。接著，利用 Hash Map 將第一個字串 `s` 當作「進貨」來統計每個字元的數量，再將第二個字串 `t` 當作「出貨」來扣除。只要發現沒看過的字元，或是數量被扣到小於 0，就代表兩者不對等。

**Python 實作 (Hash Map 字典版)：**
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False
        counter = {}
        for char in s:
            counter[char] = counter.get(char, 0) +1        
        for char in t:
            if char not in counter or counter[char] == 0:
                return False
            counter[char] -=1
        return True
            
