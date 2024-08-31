[TOC]
# Python 数据结构 速查

## 访问
根据索引去get

## 搜索
根据元素 去 寻找

## 时间复杂度
算法的执行时间和输入值 之间的关系
O(1), O(logn二分查找法), O(n), O(nlogn排序), O(n^2^)...

```python
i = 1
while (i <= n):
i = i * 2
```

循环执行一次: i = 1 * 2 = 2
循环执行两次: i = 2 * 2 = 4
循环执行三次: i = 4 * 2 = 8 
$...$
循环执行x次: i = 2^x^ 

$$
2^x \le n \\
x \le log2n
$$

## 空间复杂度
算法的存储空间和输入值之间的关系 
==算法本身占据的空间 + 算法使用的辅助空间.==

## 布尔
True: 不等于0的数
False: 0

## 数字

### 种类

1. **int**
2. **float**
3. <u>complex</u>

### 相关操作

```
a + b
a - b
a * b
a / b
a // b
a % b
abs(-2)  # 绝对值
max(1, 2, 3)
min(1, 2, 3)
pow(x, y)  # x^y
math.sqrt(x)  # import math
```

## 列表[]

### 相关操作

1. 查找 a[index] *在数组里查找很快*
2. 增加 a.append(6) *在后面追加一个append数字*
3. 更新 a[0] = 9
4. 删除 a.pop(0) *把index为0的元素 删掉* **可以返回一个值**
5. 删除 a.pop(): 如果没有参数, 默认删除最后一个

### 好用的函数

len(a), max(a), min(a), a.reverse(), a.clear(), in

```python
for x in a:
	pass
	 
for x in range(len(a)):
	pass
```

### 高级操作

```python
b = [i * i for i in a]
c = [2 * i if i > 3 else i for i in a]
```

## 元组()

只能**查找**, 无法修改,增加, 和删除

### 好用的函数

len(a), max(a), min(a), in, 

## 集合{}

### 相关操作

**所有的元素都是唯一的**
a.add(): 无序增加
a.update([4, 5...]): 往里增加(应该是可以添加在后面的)
a.remove(2): 删除2这个元素

a - b: a有b没有
a | b: a或b有
a & b: a有b也有
a ^ b: a和b中 不同时拥有的元素

## 字典k:v

###  相关操作

查询: dict["name"]: 返回value
增加: dict["platform"]: "YouTube"
更改: dict["platform"]: "BiliBili"
删除: dict.pop(key)  # 把key和value一起删掉了

```python
for key in dict:
	print(key)
	
for value in dict.values:
	print(value)
	
for k, v in dict.items():
	print(k, v)
```

## 字符串

### 相关操作
len(s), max(s), min(s)
s.count("h"), s.isupper(): 是否全部为大写字母, s.islower(), s.isdigit()
s.lower(), s.upper(), s.strip(), s.lstrip(), s.rstrip(), s.swapcase()
s.replace("a", "T")
s.split(","): 按照什么分割

## 数组 Array

**内存中有一段连续的内存, 存储一组类型相同的数据**
优点: 用索引去读索引非常得快 chua的一下定位 O(1)
缺点: 查询, 插入, 删除慢 O(n)

```python
a = []
a.append(1)  # O(1) 添加
a.append(2)  # O(1) 添加
a.append(3)  # O(1) 添加
a.insert(2, 99)  # O(n) 添加
print(a[2])  # O(1) 访问
a[2] = 100  # O(1) 更新
a.remove(100)  # O(n) 删除传入的元素
a.pop(索引值)  # O(n) 删除
a.pop()  # O(1)  删除最后一个元素
print(len(a))  # 长度

for i in a: 
	print(i)  # O(n) 遍历
	
for index, element in enumerate(a):
	print(index, element)  # O(n) 遍历
	
for i in range(0, len(a)):
	print(i, a[i])  # O(n) 遍历
	
index = a.index(2)  # 传入元素, 返回索引值 O(n)

a.sort()  # 从小到大排序 O(nlogn)
a.sort(reverse=True)  # 从大到下排序 O(nlogn)
```

## 链表 LinkedList

** 读少 写多** 
优点: 插入 和 删除 非常得快 操作本身是O(1)
缺点: 查询, 访问慢 操作本身是O(n)

```python
linkedlist = dedque()  # 也是队列的表示方法 创建链表
linkedlist.append(1)  # O(1) 添加元素
linkedlist.append(2)   # O(1) 添加元素
linkedlist.append(3)   # O(1) 添加元素
linkedlist.insert(2, 99)  # O(n) 这里面包括了一个查找“2”的动作
print(linkedlist[2])  # O(n) 一个一个访问元素 没办法计算内存
index = linkedlist.index(99)  # 传入元素, 返回索引值 O(n)
linkedlist[2] = 100  # O(n) 更新
linkedlist.remove(80)  # O(n) 传入要删除的元素
del linkedlist[2]  # O(n) 根据索引来删除
print(len(linkedlist))  # O(1) 获取长度
```

## 哈希表 Hash Table

**按照索引访问是access, 按照元素访问是search** 
看作字典的k:v
key的好处: 查询, 插入, 删除 快
缺点: 没办法通过index索引来访问元素

## 队列 Queue FIFO BFS

### 用List来表示

a.append(ending) + a.pop(0): 每次pop第一位置元素的时候, 后序元素都会陆续往前补, **耗时**

### 用deque来表示

```python
from collections import deque
q = deque([1, 2, 3])
q.append()
q.popleft()

q.pop()
q.appendleft()
q.max(), q.min(), len(q)
```

## 栈 Stack FILO DFS

### 用普通List来表示

s.append() + s.pop()

### 用deque来表示

```python
from collections import deque
s = deque([1, 2, 3])
s.append()
s.pop()

s.popleft()
s.appendleft()
s.max(), s.min(), len(s)
```

## 堆 Heap 

### 小堆 pop时永远最小值

```python
### 默认是小堆 后面的大小不确定 但头一定是最小值!
from heapq import heapify, heappush, heappop
a = [1, 2, 3]
heapify(a)
heappush(a, 40)  # 放一个值在heap里 
heappop(a)  # 删除掉(最小)值
nlargest(2, a)
nsmallest(2, a)
```

### 大堆 pop时永远最大值

## 树 Tree

**父子关系** 
**根节点** 老祖宗
**叶子节点** 没孩子的
**高度**: 某一个节点 到 叶子节点 的 最长路径
**深度**: 从根节点开始 到 要查看节点的 边数
**层**: 1, 2, 3......
**树的高度**: 从 根节点 到 叶子节点 的 最长路径

### 二叉树
普通二叉树: **每个节点最多有两个分支**
满二叉树: **除了叶子节点, 每个节点都有两个子节点**
完全二叉树: **树中的节点 从上到下 从左到右 进行编号 每个编号 与 如果当前这个二叉树是满二叉树时，位置 应该相同**

#### 二叉树 遍历
1. 前序遍历: 当前节点->左节点->右节点
2. 中序遍历: 左节点->当前节点->右节点
3. 后序遍历: 左节点->右节点->当前节点











