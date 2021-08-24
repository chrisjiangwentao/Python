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

