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
### 2. [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/#/description)
>You are given two non-empty linked lists representing two non-negative integers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.  

>You may assume the two numbers do not contain any leading zero, except the number 0 itself.  

>Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)  
>Output: 7 -> 0 -> 8  
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
public class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
       // if(l1==null) return l2;
       // if(l2==null) return l1;
        ListNode head = new ListNode(0);
        ListNode p = head;
        int tmp =0;
        while(l1!=null || l2!=null || tmp!=0){
            if(l1!=null){
                tmp+=l1.val;
                l1=l1.next;
            }
            if(l2!=null){
                tmp+=l2.val;
                l2=l2.next;
            }
          /*  if(tmp>=10){
                int carry = tmp/10;
               // p.val = tmp%10;
            }*/
             //p.val = tmp%10;
             p.next=new ListNode(tmp%10);
             tmp=tmp/10;
             p=p.next;
            // tmp=tmp/10;
        }
        return head.next;
    }
}
```
