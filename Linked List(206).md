### 206. [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/#/description)
>Reverse a singly linked list.  
----
### Java
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
 //with iteration
public class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode p = head,q = null,front = null;  
        while(p!=null){  
            q = p.next;//设置q是p结点的后继结点,即用q来保持p的后继结点  
            p.next = front;//逆转,即使p.next指向p结点的前驱结点  
            front = p;//front向后移一步  
            p = q;//p向后移一步  
        }  
        head = front;//head指向原链表的最后一个结点，完成逆转  
        return head;
    }
}


/**
//with recursive
public ListNode reverse1(ListNode head) {
        // 当为空或者本节点为末尾节点的时候
        if (head == null || head.next == null)
            return head;
        ListNode temp = head.next;
        ListNode reversedHead = reverse1(head.next);
        // 获取先前的下一个节点，让该节点指向自身
        temp.next = head;
        // 破坏以前自己指向下一个节点
        head.next = null;
        // 层层传递给最上面的
        return reversedHead;
    }
    **/
    
//Java 单链表逆转： http://blog.csdn.net/bug_moving/article/details/52742897
```
