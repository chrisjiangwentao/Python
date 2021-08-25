## 21210824

二硕申请的金融专业需要python，还是逃不掉后端呀。:(



两数之和-hashtable



nums=2，7，11，5

Target=9



if target -num in hashtable

​	return [hashtable[target-num],i]

Hashtable[nums[i]] = i



0 // 9-0

 2:0-7;0-11:0-5:0 //没有九

1// 9-1=8

7:1 //这一步有疑问，不确定哈希表的特性

2// 9-2=7 //找到7了

return hashtable hashtable[target-num], i // [7,2] //返回



知识点：hashtable会覆盖。比如已有3:0，加入3:1之后，最后hashtable只会剩下3:1，而不是两个key（3:1， 3:2）

```python
class Solution(object):
    def twoSum(self, nums1, target1):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        hashtable1 = dict()
        for i, j in enumerate(nums1):
            if target1 - j in hashtable1:
                return [hashtable1[target1 - j], i]
            hashtable1[nums1[i]] = i
        return []
```

## 20210825

l1=1,2,3,4,5

```python
while l1:
  #假设前面有个已经取出一个链表节点到num里面了，现在是1
  
	tmp.next = ListNode(num) # 1. 这里并没有给新链表的第一个节点赋值，而是跳到了第二个节点赋值
  # 2. 为什么不直接 tmp=ListNode(num)给第一个节点赋值呢
  
  tmp = tmp.next #3.然后从这里换到下一个节点，开始第二轮循环
```

空表头 dummy head



```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        dummy = result = ListNode()
        sum = 0
        while l1 or l2 or sum: #如果l1或者l2没有遍历完，还有剩下的，又或者进位不为0。
            sum += (l1.val if l1 else 0) + (l2.val if l2 else 0)
            result.next = ListNode(sum % 10) #把结果存在dummy的下一个节点，
                                             #然后看有没有进位，超过十，进一位，如果sum=5，5%10还是等于5，如果sum=12，那12%10=2。

            result = result.next #向后遍历
            sum //= 10 # 取整除，比如（9//2 =4），sum=10的时候，10//10=1，这就是一个进位，它会加到下一次（节点）循环中，另外11//10=1，19//10=1，20//10=2.
            l1 = l1.next if l1 else None
            l2 = l2.next if l2 else None
        return dummy.next
```

