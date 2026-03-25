# 📊 Array & Hash Table - Easy 題型整理

這份文件收錄了有關於陣列與雜湊表（Dictionary）的基礎題型與核心觀念。

---

## 1. Two Sum (兩數之和)
* **核心技巧**: `Hash Table` (Python `dict`)
* **時間複雜度**: $O(n)$

**解題思路與關鍵問題：**
**Q：為什麼不是先把所有值都放進字典，而是「邊找邊放」？**
1. **處理重複數值**：若陣列為 `[3, 3]` 且目標為 `6`，邊找邊放能在讀取到第二個 `3` 時，完美找到第一個 `3`，解決覆蓋衝突。
2. **提前結束 (Early Exit)**：若答案出現在前端，不需掃描完整個陣列，提升效率。
3. **防止自我匹配**：確保不會找到同一個索引的自己。

**Python 實作：**
```python
class Solution:
    def twoSum(self, nums: list[int], target: int) -> list[int]:
        pair_idx = {}
        for i, num in enumerate(nums):
            diff = target - num
            if diff in pair_idx:
                return [pair_idx[diff], i]
            pair_idx[num] = i