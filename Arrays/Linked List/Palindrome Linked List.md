Logic:)
The logic is to initially find the middle of the linked list by tortoise method and then reverse the next part after 
the middle node and then compare first half and second half using pointers if they match then LL is palindrome otherwise not.

Code:)
```cpp
class Solution {
public:
    bool isPalindrome(ListNode* head) {
        if((head == NULL)||(head->next == NULL)) return true;
        ListNode *slow = head;
        ListNode *fast = head;
        while((fast->next != NULL)&&(fast->next->next != NULL))
        {
            slow=slow->next;
            fast=fast->next->next;
        }
        slow->next = reverseLL(slow->next);
        slow=slow->next;
        while(slow != NULL)
        {
            ListNode *temp1 = head;
            while(slow != NULL)
            {
                if(slow->val != temp1->val) return false;
                slow=slow->next;
                temp1=temp1->next;
            }
        }

        return true;
    }

    ListNode* reverseLL(ListNode *temp)
    {
            ListNode *dummy = NULL;
            ListNode *nextNode = NULL;
            while(temp != NULL)
            {
                nextNode = temp->next;
                temp->next = dummy;
                dummy = temp;
                temp = nextNode;
            }
            return dummy;
    }
};
```
Complexity:
T.C: O(N)
S.C: O(1)