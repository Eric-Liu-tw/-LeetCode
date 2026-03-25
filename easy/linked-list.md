# 🔗 Linked List - Easy 題型整理

這份文件收錄了有關於單向鏈結串列的基礎題型與指標操作。

---

## 21. Merge Two Sorted Lists (合併兩個有序鏈表)
* **核心技巧**: `Dummy Node` (虛擬頭節點)、`Two Pointers` (雙指標)
* **時間複雜度**: $O(n + m)$

**解題思路與關鍵問題：**
**Q：為什麼需要 `ans = ListNode()` (Dummy Node)？**
合併過程中 `cur` 指標會不斷向後移動，如果沒有 `ans` 固定在原點，最後會找不到新串列的頭。回傳時只需 `return ans.next`。

**Q：為什麼移動位置要寫 `list1 = list1.next` 而不是 `list1.val = list1.next`？**
`.val` 存的是數字，`.next` 存的是節點物件。我們是在「重組」現有的節點（搬運整個人），而不是修改節點內部的數值。

**Python 實作：**
```python
class Solution:
    def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
        ans = ListNode()
        cur = ans
        
        while list1 and list2:
            if list1.val > list2.val:
                cur.next = list2
                list2 = list2.next
            else:
                cur.next = list1
                list1 = list1.next
            cur = cur.next
            
        cur.next = list1 if list1 else list2
        return ans.next