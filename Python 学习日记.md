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

## 20210826



```python
class Solution(object):
    def findRepeatNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        hashSet = set()
        for num in nums:
            if num in hashSet: return num
            hashSet.add(num)
        return -1
```



## 20210827





```python
class Solution(object):
    def replaceSpace(self, s):
        """
        :type s: str
        :rtype: str
        """
        res = []
        for c in s:
            if c == ' ': res.append("%20")
            else: res.append(c)
        return "".join(res)
```



## 20210828





```python
class Solution(object):
    def printNumbers(self, n):
        """
        :type n: int
        :rtype: List[int]
        """
        return [i for i in range(1, 10**n)]

        #  range(start, stop[, step])
        # start: 计数从 start 开始。默认是从 0 开始。例如range（5）等价于range（0， 5）
        # stop: 计数到 stop 结束，但不包括 stop。例如：range（0， 5） 是[0, 1, 2, 3, 4]没有5 
        # step：步长，默认为1。例如：range（0， 5） 等价于 range(0, 5, 1)
        
        # range 在 for 中的使用，循环出runoob 的每个字母
        # x = 'hello'
        # for i in range(len(x)) :
        # print(x[i])
        # 结果：h，e，l，l，o
```



## 20210829





```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def reversePrint(self, head):
        """
        :type head: ListNode
        :rtype: List[int]
        """
        return self.reversePrint(head.next) + [head.val] if head else []
        
        # 递推阶段： 每次传入 head.next ，以 head == None（即走过链表尾部节点）为递归终止条件，此时返回空列表 [] 。

        # 回溯阶段： 利用 Python 语言特性，递归回溯时每次返回 当前 list + 当前节点值 [head.val] ，即可实现节点的倒序输出。
```





## 20210830





```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None
class Solution(object):
    def deleteNode(self, head, val):
        """
        :type head: ListNode
        :type val: int
        :rtype: ListNode
        """
        if head.val == val: return head.next # 如果要删除的值和头节点的值相同，则返回下一个节点，等同于删除头节点 （删除头节点）
        pre, cur = head, head.next # 初始化节点
        while cur and cur.val != val: # 如果当前的节点cur不为空，或者节点的值不等于要删除的值就继续循环，如果当前节点的值等于要删除的值，退出循环。
            pre, cur = cur, cur.next # 调换节点位置，节点往后移一位
        if cur: pre.next = cur.next # 如果cur指向某节点，前一个节点等于下一个节点 （删除当前节点）
        return head # 返回修改后的链表

```





## 20210831



```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def reverseList(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        # 迭代
        cur, pre = head, None
        while cur: # cur等于null的时候跳出循环
            tmp = cur.next # 暂存当前节点的后续节点 cur.next
            cur.next = pre # 修改当前节点的next 引用指向
            pre = cur      # pre 暂存 cur
            cur = tmp      # cur 访问下一节点
        return pre
```



## 20210901





```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def mergeTwoLists(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        cur = dum = ListNode(0)
        while l1 and l2:
            if l1.val < l2.val:
                cur.next, l1 = l1, l1.next
            else:
                cur.next, l2 = l2, l2.next
            cur = cur.next
        cur.next = l1 if l1 else l2
        return dum.next
```



## 20210902



```python
class Solution(object):
    def removeElement(self, nums, val):
        """
        :type nums: List[int]
        :type val: int
        :rtype: int
        """
        a = 0
        b = 0

        while a < len(nums):
            if nums[a] != val:
                nums[b] = nums[a]
                b += 1
            a += 1
        return b
```



## 20210903



```python
class Solution(object):
    def merge(self, A, m, B, n):
        """
        :type A: List[int]
        :type m: int
        :type B: List[int]
        :type n: int
        :rtype: None Do not return anything, modify A in-place instead.
        """
        sorted = []
        pa, pb = 0, 0 # 两个数组的下标
        while pa < m or pb < n:
            if pa == m: # 这里表示a走完了，所以把剩下的b直接加到排序里
                sorted.append(B[pb])
                pb += 1
            elif pb == n: # 这里表示b走完了，把剩下的a加到排序里
                sorted.append(A[pa])
                pa += 1
            elif A[pa] < B[pb]:
                sorted.append(A[pa])
                pa += 1
            else:
                sorted.append(B[pb])
                pb += 1
        A[:] = sorted # 这个地方不是特别理解！！！
```



## 20210904: Fibonacci sequence

- 斐波那契数列以如下被以递推的方法定义：*F*(0)=0，*F*(1)=1, *F*(n)=*F*(n - 1)+*F*(n - 2)（*n* ≥ 2，*n* ∈ N*）
- **斐波那契数列**：0，1，1，2，3，5，8，13，21，34，55，89，144，233，377，610，987，1597，2584，4181，6765，10946，17711，28657，46368，，，，，，，，，，，，，，，这个数列从第3项开始，每**一项都等于前两项之和**。-----**这个超级超级重要**



#### 动态规划解析：

**状态定义：** 设 dp*d**p* 为一维数组，其中 dp[i]*d**p*[*i*] 的值代表 斐波那契数列第 i*i* 个数字 。

转移方程： dp[i+1]=dp[i]+dp[i−1]，即对应数列定义 f(n+1)=f(n)+f(n−1) ；

**初始状态：dp[0]=0, dp[1]=1 ，即初始化前两个数字；

```python
class Solution(object):
    def fib(self, n):
        """
        :type n: int
        :rtype: int
        """
        MOD = 10 ** 9 + 7
        if n < 2:
            return n
        p, q, r = 0, 0, 1
        for i in range(2, n + 1):
            p = q
            q = r
            r = (p + q) % MOD
        return r
```

1e9+7=1乘以10的9次方加7=1000000007

## 20210904: mod and rem (取模和取余)

取模运算和取余运算是两个概念，虽然他们有重叠部分，但又不一致。不一致的地方在于对负整数进行除法时，操作不一样。
对于整数 a 和 b，进行取模运算和取余运算可以总结分为 2 个步骤：

1. 计算整数商： c = 取整（a / b）;
2. 计算模或余数：r = a - c * b

两者的区别就在于第 1 步中的计算整数商不同，取模是向负无穷方向取整（即向下取整），取余是向 0 方向取整（即商大于 0 时向下取整，小于0时向上取整）。

```python
# 取模，Python中可直接用%，计算模，r = a % b
 2 def mod(a, b):    
 3     c = a // b
 4     r = a - c * b
 5     return r
 6 
 7 # 取余 
 8 def rem(a, b):
 9     c = int(a / b)
10     r = a - c * b
11     return r

# 5%10
# a=5 b=10
# c= 0
# r=5-0*5=5
```

 

## 20210905





```python
class Solution(object):
    def numWays(self, n):
        """
        :type n: int
        :rtype: int
        """
        a, b = 1, 1
        for _ in range(n):
            a, b = b, a + b
        return a % 1000000007
```



## 20210906



```python
class Solution(object):
    def findJudge(self, n, trust):
        """
        :type n: int
        :type trust: List[List[int]]
        :rtype: int
        """
        in_degree = [0] * (n + 1)
        out_degree = [0] * (n + 1)
        for a, b in trust:
            in_degree[b] += 1
            out_degree[a] += 1
        for i in range(1, n + 1):
            if in_degree[i] == n - 1 and out_degree[i] == 0:
                return i
        return -1

```





## 20210907





```python
class Solution(object):
    def missingNumber(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        return sum(range(len(nums)+1)) - sum(nums)

        # 本来求和值: sum(range(len(nums)+1))
        # 输入求和值： sum(nums)
        # 缺失值：sum(range(len(nums)+1)) - sum(nums)
```



## 20210908





```python
class Solution(object):
    def distributeCandies(self, candyType):
        """
        :type candyType: List[int]
        :rtype: int
        """
        return min(len(set(candyType)), len(candyType)/2)
```



## 20210909: Basic Python syntax



### 数字(Number)类型

python中数字有四种类型：整数、布尔型、浮点数和复数。

- **int** (整数), 如 1, 只有一种整数类型 int，表示为长整型，没有 python2 中的 Long。
- **bool** (布尔), 如 True。
- **float** (浮点数), 如 1.23、3E-2
- **complex** (复数), 如 1 + 2j、 1.1 + 2.2j





### 字符串截取：

索引值以 0 为开始值，-1 为从末尾的开始位置。

Python中的字符串有两种索引方式，从左往右以0开始，从右往左以-1开始

![img](https://static.runoob.com/wp-content/uploads/123456-20200923-1.svg)

```python
str='123456789'
 
print(str)                 # 输出字符串
print(str[0:-1])           # 输出第一个到倒数第二个的所有字符
print(str[0])              # 输出字符串第一个字符
print(str[2:5])            # 输出从第三个开始到第五个的字符
print(str[2:])             # 输出从第三个开始后的所有字符
print(str[1:5:2])          # 输出从第二个开始到第五个且每隔一个的字符（步长为2）
print(str * 2)             # 输出字符串两次
print(str + '你好')         # 连接字符串
print('------------------------------')
print('hello\nrunoob')      # 使用反斜杠(\)+n转义特殊字符
print(r'hello\nrunoob')     # 在字符串前面添加一个 r，表示原始字符串，不会发生转义

print('\n')       # 输出空行

print(r'\n')      # 输出 \n


'''
结果：
123456789
12345678
1
345
3456789
24
123456789123456789
123456789你好
------------------------------
hello
runoob
hello\nrunoob
空行
\n
'''
```

## 20210915 List

![img](https://www.runoob.com/wp-content/uploads/2014/08/list_slicing1_new1.png)

```python
a = [1, 2, 3, 4, 5, 6]
a[0] = 9
a[2:5] = [13, 14, 15]
a
# [9, 2, 13, 14, 15, 6]
a[2:5] = []   # 将对应的元素值设置为 [] 
a
# [9, 2, 6]
```

![image-20210915215459791](/Users/wentao/Library/Application Support/typora-user-images/image-20210915215459791.png)



### 翻转字符串：

```python
def reverseWords(input): 
      
    # 通过空格将字符串分隔符，把各个单词分隔为列表
    inputWords = input.split(" ") 
  
    # 翻转字符串
    # 假设列表 list = [1,2,3,4],  
    # list[0]=1, list[1]=2 ，而 -1 表示最后一个元素 list[-1]=4 ( 与 list[3]=4 一样) 
    # inputWords[-1::-1] 有三个参数
    # 第一个参数 -1 表示最后一个元素
    # 第二个参数为空，表示移动到列表末尾
    # 第三个参数为步长，-1 表示逆向
    inputWords=inputWords[-1::-1] 
  
    # 重新组合字符串
    output = ' '.join(inputWords) 
      
    return output 
  
if __name__ == "__main__": 
    input = 'I like runoob'
    rw = reverseWords(input) 
    print(rw)
    # runoob like I
```

### Tuple:

tuple的元素不可改变，但它可以包含可变的对象，比如list列表。 



### Python3 的六个标准数据类型中：

- **不可变数据（3 个）：**Number（数字）、String（字符串）、Tuple（元组）；
- **可变数据（3 个）：**List（列表）、Dictionary（字典）、Set（集合）。

内置的 type() 函数可以用来查询变量所指的对象类型。

```python
a, b, c, d = 20, 5.5, True, 4+3j
print(type(a), type(b), type(c), type(d))

# <class 'int'> <class 'float'> <class 'bool'> <class 'complex'>
```



### del

可以通过使用del语句删除单个或多个对象。例如：

```python
del var
del var_a, var_b
# del var1[,var2[,var3[....,varN]]]
```



## 20210910 hashmap底层原理



**HashMap是一个用于存储Key-Value键值对的集合，每一个键值对也叫做Entry。这些个键值对（Entry）分散存储在一个数组当中，这个数组就是HashMap的主干。**



对于HashMap，我们最常使用的是两个方法：**Get** 和 **Put**。

1. **Put方法的原理**

   比如调用 hashMap.put("apple", 0) ，插入一个Key为“apple"的元素。这时候我们需要利用一个哈希函数来确定Entry的插入位置（index）：

   **index = Hash（“apple”）**

   假定最后计算出的index是2，那么结果如下：

   ![img](https://pic2.zhimg.com/80/v2-6f0c2ee36a675192f5bc629f404881e9_1440w.jpg)

   

   但是，因为HashMap的长度是有限的，当插入的Entry越来越多时，再完美的Hash函数也难免会出现index冲突的情况。比如下面这样：

   ![img](https://pic3.zhimg.com/80/v2-81c6c3dc75ad7f1fee6666aad666de8a_1440w.jpg)

   这时候该怎么办呢？我们可以利用**链表**来解决。

   HashMap数组的每一个元素不止是一个Entry对象，也是一个链表的头节点。每一个Entry对象通过Next指针指向它的下一个Entry节点。当新来的Entry映射到冲突的数组位置时，只需要插入到对应的链表即可：

   ![img](https://pic3.zhimg.com/80/v2-cb404baffd8419765c3d0a41555921fa_1440w.jpg)

   之所以把Entry6放在头节点，是因为HashMap的发明者认为，**后插入的Entry被查找的可能性更大**， jdk1.8是尾插，jdk1.7是头插。 1.8之后加入了红黑树，当链表长度为8转换为红黑树。



2. Get方法的原理

   使用Get方法根据Key来查找Value的时候，首先会把输入的Key做一次Hash映射，得到对应的index：

   index = Hash（“apple”）

   由于刚才所说的Hash冲突，同一个位置有可能匹配到多个Entry，这时候就需要顺着对应链表的头节点，一个一个向下来查找。假设我们要查找的Key是“apple”：

![img](https://pic4.zhimg.com/80/v2-e56018da68f0be0945a03971a097f41f_1440w.jpg)

​		第一步，我们查看的是头节点Entry6，Entry6的Key是banana，显然不是我们要找的结果。

​		第二步，我们查看的是Next节点Entry1，Entry1的Key是apple，正是我们要找的结果。



3. 补充说明

   HashMap的初始默认长度是16，同时每次扩充（或手动初始化）必需设置长度为2的幂（为了服务于从key映射到index的Hash算法）。

   取模运算：**index = HashCode（Key） % Length ?**

   位运算：**index = HashCode（Key） & （Length** **- 1）**

   1.计算book的hashcode，结果为十进制的3029737，二进制的101110001110101110 1001。

   2.假定HashMap长度是默认的16，计算Length-1的结果为十进制的15，二进制的1111。

   3.把以上两个结果做**与运算**，101110001110101110 1001 & 1111 = 1001，十进制是9，所以 index=9。

   可以说，Hash算法最终得到的index结果，完全取决于Key的Hashcode值的最后几位。

   当HashMap长度为10或者其他非2的幂的时候，有些index结果的出现几率会更大，而有些index结果永远不会出现（比如0111），不符合Hash算法均匀分布的原则。



