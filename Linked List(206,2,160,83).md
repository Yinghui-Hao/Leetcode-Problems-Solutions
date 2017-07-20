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
### 160. [Intersection of Two Linked Lists](https://leetcode.com/problems/intersection-of-two-linked-lists/#/description)
>Write a program to find the node at which the intersection of two singly linked lists begins.
----
### Java
```
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        ListNode p1 = headA, p2 = headB;
        int len1 = 0, len2 = 0;
        while (p1 != null) {
            p1 = p1.next;
            len1++;
        }
        while (p2 != null) {
            p2 = p2.next;
            len2++;
        }
        p1 = headA;
        p2 = headB;
        if (len1 > len2) {
            for (int i = 0;i < len1 - len2; i++) {
                p1 = p1.next;
            }
        } else {
            for (int i = 0;i < len2 - len1; i++) {
                p2 = p2.next;
            }
        }
        while (p1 != p2) {
            p1 = p1.next;
            p2 = p2.next;
        }
        return p1;    
    }
}

/*
Solution 1:
1, Get the length of the two lists.

2, Align them to the same start point.

3, Move them together until finding the intersection point, or the end null

public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
    int lenA = length(headA), lenB = length(headB);
    // move headA and headB to the same start point
    while (lenA > lenB) {
        headA = headA.next;
        lenA--;
    }
    while (lenA < lenB) {
        headB = headB.next;
        lenB--;
    }
    // find the intersection until end
    while (headA != headB) {
        headA = headA.next;
        headB = headB.next;
    }
    return headA;
}

private int length(ListNode node) {
    int length = 0;
    while (node != null) {
        node = node.next;
        length++;
    }
    return length;
}

Solution 2:
public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
    //boundary check
    if(headA == null || headB == null) return null;
    
    ListNode a = headA;
    ListNode b = headB;
    
    //if a & b have different len, then we will stop the loop after second iteration
    while( a != b){
    	//for the end of first iteration, we just reset the pointer to the head of another linkedlist
        a = a == null? headB : a.next;
        b = b == null? headA : b.next;    
    }
    
    return a;
}
You can prove that: say A length = a + c, B length = b + c, after switching pointer, pointer A will move another b + c steps, pointer B will move a + c more steps, since a + c + b + c = b + c + a + c, it does not matter what value c is. Pointer A and B must meet after a + c + b (b + c + a) steps. If c == 0, they meet at NULL.
Thanks, hpplayer. This solution is very smart.
*/
```
### 83. [Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/#/description)
> Given a sorted linked list, delete all duplicates such that each element appear only once.

>For example,  
>Given 1->1->2, return 1->2.  
>Given 1->1->2->3->3, return 1->2->3.   
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
    public ListNode deleteDuplicates(ListNode head) {
        ListNode current = head;
        while(current != null){
            if(current.next == null) break;
            if(current.val == current.next.val){
                current.next = current.next.next;
            }else{//[1,1,1]would output [1,1] not [1] without else
                current = current.next;
            }
            
        }
        return head;
    }
}
//sorted, so the same element must be continue.
/*
public ListNode deleteDuplicates(ListNode head) {
        if(head == null || head.next == null)return head;
        head.next = deleteDuplicates(head.next);
        return head.val == head.next.val ? head.next : head;
}
*/
```
