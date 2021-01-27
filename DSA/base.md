##

## 2 链表
**类型**
- 单链表
- 双链表
- 循环链表

### 2.1 基础语法
**定义**
```C++
// C++
// 单链表
struct ListNode {
    int val;  // 节点上存储的元素
    ListNode *next;  // 指向下一个节点的指针
    ListNode(int x) : val(x), next(NULL) {}  // 节点的构造函数
};
```
**链表的操作，插入、删除**

> [Leetcode:203 移除链表元素](https://leetcode-cn.com/problems/remove-linked-list-elements/) 
> 删除链表中值为val的节点
```C++
class Solution {
public:
    ListNode* removeElements(ListNode* head, int val) {
        ListNode* dummyHead = new ListNode(0); // 设置一个虚拟头结点
        dummyHead->next = head; // 将虚拟头结点指向head，这样方面后面做删除操作
        ListNode* cur = dummyHead;

        while (cur->next != NULL) {
            if(cur->next->val == val) {
                ListNode* tmp = cur->next;
                cur->next = cur->next->next;
                delete tmp;
            } else {
                cur = cur->next;
            }
        }
        return dummyHead->next;
    }
};
```

> [Leetcode707：设计链表](https://leetcode-cn.com/problems/design-linked-list/)
> 实现链表的5个操作

> [Leetcode206：反转链表](https://leetcode-cn.com/problems/reverse-linked-list/)
> 简单