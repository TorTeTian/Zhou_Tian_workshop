# Assignment #7: April 月考

Updated 1557 GMT+8 Apr 3, 2024

2024 spring, Complied by 周添 物理学院



## 1. 题目

### 27706: 逐词倒放

http://cs101.openjudge.cn/practice/27706/



代码

```python
line = [i for i in input().split()]
line = reversed(line)
for j in line:
    print(j, end=' ')

```

![image-20240407133311033](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240407133311033.png)



### 27951: 机器翻译

http://cs101.openjudge.cn/practice/27951/



代码

```python
import queue

m, n = map(int, input().split())
nums = [int(i) for i in input().split()]
q = queue.Queue()
counter = 0
for i in nums:
    if i not in q.queue:
        counter += 1
        if q.qsize() == m:
            q.get()
        q.put(i)
print(counter)

```

![image-20240407140027709](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240407140027709.png)



### 27932: Less or Equal

http://cs101.openjudge.cn/practice/27932/



代码

```python
import heapq

m, n = map(int, input().split())
nums = [int(i) for i in input().split()]
heapq.heapify(nums)
if n == 0:
    k = heapq.heappop(nums)-1
    if k <= 0:
        print(-1)
    else:
        print(k)
else:
    for i in range(n - 1):
        heapq.heappop(nums)
    a = heapq.heappop(nums)
    if n == m:
        print(a)
    else:
        b = heapq.heappop(nums)
        if a < b:
            print(a)
        else:
            print(-1)

```



![image-20240407141325231](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240407141325231.png)



### 27948: FBI树

http://cs101.openjudge.cn/practice/27948/



代码

```python
class Node:
    def __init__(self, v):
        self.v = v
        self.left = None
        self.right = None


def f_or_b_or_i(string):
    if string == '1'*len(string):
        return 'I'
    elif string == '0'*len(string):
        return 'B'
    else:
        return 'F'


def build_tree(s):
    if len(s) == 1:
        return Node(f_or_b_or_i(s))
    node = Node(f_or_b_or_i(s))
    mid = len(s)//2
    node.left = build_tree(s[:mid])
    node.right = build_tree(s[mid:])
    return node


def postorder_traversal(root):
    if root is None:
        return []

    left = postorder_traversal(root.left)
    right = postorder_traversal(root.right)

    return left + right + [root.v]


a = int(input())
st = input()
root = build_tree(st)
y = postorder_traversal(root)
print(''.join(y))


```



![image-20240407151456276](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240407151456276.png)

### 27925: 小组队列

http://cs101.openjudge.cn/practice/27925/



代码

```python
from collections import deque
t=int(input())
groups=dict()
for i in range(t):
    new_g=list(map(int,input().split()))
    for member in new_g:
        groups[member]=i
in_queue=deque()
seq=dict()
while True:
    order=input()
    if order=='STOP':
        break
    else:
        if order[0]=='E':
            new=int(order.split()[1])
            group=groups[new]
            if group in in_queue:
                seq[group].append(new)
            else:
                in_queue.append(group)
                seq[group]=deque()
                seq[group].append(new)

        else:
            head=in_queue[0]
            print(seq[head].popleft())
            if len(seq[head])==0:
                seq.pop(head)
                in_queue.popleft()

```

![image-20240408224519956](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240408224519956.png)







### 27928: 遍历树

http://cs101.openjudge.cn/practice/27928/





代码

```python
import heapq
class Node:
    def __init__(self,value):
        self.value=value
        self.child=[]
    def __lt__(self,other):
        return self.value<other.value
def build_tree(all_info,i):
    if len(all_info[i])==0:
        return Node(i)
    root=Node(i)
    for child in all_info[i]:
        root.child.append(build_tree(all_info,child))
    return root

def traversal(root):
    if len(root.child)==0:
        print(root.value)
        return
    childs=root.child
    heapq.heapify(childs)
    flag=0
    while childs:
        min_child=heapq.heappop(childs)
        #print(min_child.value)
        if flag==0:
            if root.value<min_child.value:
                print(root.value)
                flag=1
                traversal(min_child)
            else:
                traversal(min_child)
        else:
            traversal(min_child)
    if flag==0:
        print(root.value)
n=int(input())
all_info=dict()
for _ in range(n):
    info=list(map(int,input().split()))
    root=info[0]
    all_info[root]=info[1:]
keys=all_info.keys()
not_root=set()
for i in keys:
    not_root.update(all_info[i])

for i in keys:
    if i not in not_root:
        root_num=i
        break
#print(all_info)
root=build_tree(all_info,root_num)
traversal(root)
```



![image-20240408224438765](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240408224438765.png)





## 2. 学习总结和收获

前面的有点简单，最后两题不太会





