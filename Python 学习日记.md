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

## 20210915 Python List

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

如果**第三个参数为负数表示逆向读取**，以下实例用于翻转字符串：

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

**如果第三个参数为负数表示逆向读取，以下实例用于翻转字符串：**

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



## 20210918 二进制运算



### 加法

“逢二进一”规则，二进制数加法的法则为：

0+0=0
0+1=1+0=1
1+1=0　（进位为1） 
1+1+1=1 （进位为1）

1110和1011相加过程如下

![img](https://bkimg.cdn.bcebos.com/pic/d62a6059252dd42a008715670a3b5bb5c8eab86b?x-bce-process=image/resize,m_lfit,w_220,h_220,limit_1/format,f_auto)



### 减法

“借一有二”的规则，二进制数减法的法则为：

0－0=0

1－1=0

1－0=1

0－1=1 （借位为1）

例如：1101减去1011的过程如下：

[![img](https://bkimg.cdn.bcebos.com/pic/faedab64034f78f03c708d3f70310a55b2191c86?x-bce-process=image/resize,m_lfit,w_220,h_220,limit_1/format,f_auto)



### 乘法

二进制数乘法过程可仿照十进制数乘法进行。但由于二进制数只有0或1两种可能的乘数位，导致二进制乘法更为简单。二进制数乘法的法则为：

0×0=0

0×1=1×0=0

1×1=1

例如：1001和1010相乘的过程如下：

[![img](https://bkimg.cdn.bcebos.com/pic/d1a20cf431adcbef3eda69caa5af2edda2cc9f0b?x-bce-process=image/resize,m_lfit,w_220,h_220,limit_1/format,f_auto)

由低位到高位，用乘数的每一位去乘被乘数，若乘数的某一位为1，则该次部分积为被乘数；若乘数的某一位为0，则该次部分积为0。某次部分积的最低位必须和本位乘数对齐，所有部分积相加的结果则为相乘得到的乘积。



### 除法

二进制数除法与十进制数除法很类似。可先从被除数的最高位开始，将被除数（或中间余数）与除数相比较，若被除数（或中间余数）大于除数，则用被除数（或中间余数）减去除数，商为1，并得相减之后的中间余数，否则商为0。再将被除数的下一位移下补充到中间余数的末位，重复以上过程，就可得到所要求的各位商数和最终的余数。

例如：100110÷110的过程如下：

[![img](https://bkimg.cdn.bcebos.com/pic/4d086e061d950a7bf4d0590803d162d9f3d3c911?x-bce-process=image/resize,m_lfit,w_220,h_220,limit_1/format,f_auto)

所以，100110÷110=110余10。

说明：乘除法分原码乘法和补码乘法。



## 20210918 二进制逻辑运算



### “或”运算

又称为逻辑加，可用符号“+”或“∨”来表示。逻辑“或”运算的规则如下：

0+0=0或0∨0=0

0+1=1或0∨1=1

1+0=1或1∨0=1

1+1=1或1∨1=1

可见，两个相“或”的逻辑变量中，**只要有一个为1，“或”运算的结果就为1。仅当两个变量都为0时，或运算的结果才为0。**计算时，要特别注意和算术运算的加法加以区别。

例如：3|5即 0000 0011| 0000 0101 = 0000 0111，因此，3|5的值得7。　

注意：负数按补码形式参加按位或运算。

#### 或运算的用途：

1）常用来对一个数据的某些位设置为1

比如将数 X=1010 1110 的低4位设置为1，只需要另找一个数Y，令Y的低4位为1，其余位为0，即Y=0000 1111，然后将X与Y进行按位或运算（X|Y=1010 1111）即可得到。



### “与”运算

又称为逻辑乘，常用符号“×”或“· ”或“∧”表示。“与”运算遵循如下运算规则：

0×1=0或0·1=0或0∧1=0

1×0=0或1·0=0或1∧0=0

1×1=1或1·1=1或1∧1=1

可见，两个相“与”的逻辑变量中，**只要有一个为0，“与”运算的结果就为0。仅当两个变量都为1时，“与”运算的结果才为1。**

例如：3&5 即 0000 0011& 0000 0101 = 0000 0001，因此 3&5 的值得1。

注意：负数按补码形式参加按位与运算。

#### **与运算的用途：**

1）清零

如果想将一个单元清零，即使其全部二进制位为0，只要与一个各位都为零的数值相与，结果为零。

2）取一个数的指定位

比如取数 X=1010 1110 的低4位，只需要另找一个数Y，令Y的低4位为1，其余位为0，即Y=0000 1111，然后将X与Y进行按位与运算（X&Y=0000 1110）即可得到X的指定位。

3）判断奇偶

只要根据最未位是0还是1来决定，为0就是偶数，为1就是奇数。因此可以用if ((a & 1) == 0)代替if (a % 2 == 0)来判断a是不是偶数。



### “非”运算

取反运算符

又称为逻辑否定，实际上就是将原逻辑变量的状态求反，其运算规则如下：

可见，在变量的上方加一横线表示“非”。逻辑变量为0时，“非”运算的结果为1。逻辑变量为1时，“非”运算的结果为0。

总结：对一个二进制数按位取反，即将0变1，1变0。

#### 异或运算的用途：

1）使一个数的最低位为零

使a的最低位为0，可以表示为：a & ~1。~1的值为 1111 1111 1111 1110，再按"与"运算，最低位一定为0。因为" ~"运算符的优先级比算术运算符、关系运算符、逻辑运算符和其他运算符都高。

7.左移运算符（<<）

定义：将一个运算对象的各二进制位全部左移若干位（左边的二进制位丢弃，右边补0）。

设 a=1010 1110，a = a<< 2 将a的二进制位左移2位、右补0，即得a=1011 1000。

若左移时舍弃的高位不包含1，则每左移一位，相当于该数乘以2。

8.右移运算符（>>）

定义：将一个数的各二进制位全部右移若干位，正数左补0，负数左补1，右边丢弃。

例如：a=a>>2 将a的二进制位右移2位，左补0 或者 左补1得看被移数是正还是负。

操作数每右移一位，相当于该数除以2。



### “异或”运算

“异或”运算，常用符号“”或“”来表示，其运算规则为：

00=0 或 00=0

01=1 或 01=1

10=1 或 10=1

11=0 或 11=0

可见：两个相“异或”的逻辑运算变量取值相同时，“异或”的结果为0。取值相异时，“异或”的结果为1

总结：参加运算的两个对象，如果两个相应位相同为0，相异为1。

异或的几条性质:

- 1、交换律
- 2、结合律 (a^b)^c == a^(b^c)
- 3、对于任何数x，都有 x^x=0，x^0=x
- 4、自反性: a^b^b=a^0=a;



#### 异或运算的用途：

1）翻转指定位

比如将数 X=1010 1110 的低4位进行翻转，只需要另找一个数Y，令Y的低4位为1，其余位为0，即Y=0000 1111，然后将X与Y进行异或运算（X^Y=1010 0001）即可得到。

2）与0相异或值不变

例如：1010 1110 ^ 0000 0000 = 1010 1110

3）交换两个数

```
void Swap(int &a, int &b){
    if (a != b){
        a ^= b;
        b ^= a;
        a ^= b;
    }
}
```



### 例子

以上仅就逻辑变量只有一位的情况得到了逻辑“与”、“或”、“非”、“异或”运算的运算规则。当逻辑变量为多位时，可在两个逻辑变量对应位之间按上述规则进行运算。特别注意，所有的逻辑运算都是按位进行的，位与位之间没有任何联系，即不存在算术运算过程中的进位或借位关系。下面举例说明 [2] 。

【例1.1】 如两变量的取值 *X*=00FFH，*Y*=5555H

求*Z*1=*X*∧*Y*；*Z*2=*X*∨*Y*；*Z*3=；*Z*4=*X**Y*的值。

解：	*X*=0000 0000 1111 1111

​			*Y*=0101 0101 0101 0101

与运算 ：0000 0000 0101 0101

则：*Z*1=0000 0000 0101 0101=0055H



解：	*X*=0000 0000 1111 1111

​			*Y*=0101 0101 0101 0101

或运算：0101 0101 1111 1111

​	     *Z*2=0101 0101 1111 1111=55FFH



*Z*3=1111 1111 0000 0000=FF00H

*Z*4=0101 0101 1010 1010=55AAH



### 复合赋值运算符

```
&=        例：a&=b    相当于     a=a&b

|=        例：a|=b    相当于     a=a|b

>>=      例：a>>=b   相当于     a=a>>b

<<=      例：a<<=b     相当于      a=a<<b

^=        例：a^=b    相当于   a=a^b
```

运算规则：和前面讲的复合赋值运算符的运算规则相似。

不同长度的数据进行位运算：如果两个不同长度的数据进行位运算时，系统会将二者按右端对齐，然后进行位运算。

以"与运算"为例说明如下：我们知道在C语言中long型占4个字节，int型占2个字节，如果一个long型数据与一个int型数据进行"与运算"，右端对齐后，左边不足的位依下面三种情况补足，

- 1）如果整型数据为正数，左边补16个0。
- 2）如果整型数据为负数，左边补16个1。
- 3）如果整形数据为无符号数，左边也补16个0。
- 如：long a=123；int b=1；计算a& b。

- 

- 如：long a=123；int b=-1；计算a& b。

- 如：long a=123；unsigned intb=1；计算a & b。   
