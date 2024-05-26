# Assignment #3: March月考

Updated 1537 GMT+8 March 6, 2024

2024 spring, Complied by 周添 物理学院



## 1. 题目

**02945: 拦截导弹**

http://cs101.openjudge.cn/practice/02945/



##### 代码

```python
n = int(input())
a = [int(i) for i in input().split()]
b = [1]*n
for i in range(1, n):
    for j in range(i):
        if a[i] <= a[j]:
            b[i] = max(b[i], b[j]+1)
print(max(b))


```



![image-20240307160610493](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240307160610493.png)





**04147:汉诺塔问题(Tower of Hanoi)**

http://cs101.openjudge.cn/practice/04147



##### 代码

```python
def hanoi(n, a, b, c):
    if n == 1:
        print(f"{n}:{a}->{c}")
    else:
        hanoi(n-1, a, c, b)
        print(f"{n}:{a}->{c}")
        hanoi(n-1, b, a, c)


n, a, b, c = map(str, input().split())
n = int(n)

hanoi(n, a, b, c) 

```



![image-20240307163027565](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240307163027565.png)





**03253: 约瑟夫问题No.2**

http://cs101.openjudge.cn/practice/03253



##### 代码

```python
def josephus_sequence(n, p, m):
    result = []
    children = list(range(1, n + 1))
    idx = p - 1

    while len(children) > 0:
        idx = (idx + m - 1) % len(children)
        result.append(children.pop(idx))

    return result

input_data = []
while True:
    line = input().strip()
    if line == "0 0 0":
        break
    n, p, m = map(int, line.split())
    input_data.append((n, p, m))

for n, p, m in input_data:
    sequence = josephus_sequence(n, p, m)
    output = ','.join(map(str, sequence))
    print(output)
```



![image-20240307194253383](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240307194253383.png)



**21554:排队做实验 (greedy)v0.2**

http://cs101.openjudge.cn/practice/21554

##### 代码

```python
a=int(input())
c=[int(i) for i in input().split()]
d=[[c[i],i] for i in range(a)]
d.sort(key=lambda x:(x[0],x[1]))
loc=[]
av=0
for i in range(a):
    loc.append(d[i][1]+1)
    av+=d[i][0]*(a-1-i)/a
for i in loc:
    print(i,end=' ')
print()
print('%.2f'%av)

```



![image-20240307194352116](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240307194352116.png)

**19963:买学区房**

http://cs101.openjudge.cn/practice/19963

##### 代码

```python
def middle(a):
    a_len = len(a)
    if len(a) % 2 == 1:
        return a[int((a_len+1)/2-1)]
    else:
        return (a[int(a_len/2)]+a[int(a_len/2)-1])/2


n = int(input())
xys = [i for i in input().split()]
prices = [int(i) for i in input().split()]

distances = []
for xy in xys:
    x, y = map(int, xy[1:-1].split(','))
    distances.append(x+y)

goodness = [distances[i]/prices[i] for i in range(n)]

goodness_m = middle(sorted(goodness))
prices_m = middle(sorted(prices))

answer = 0

for i in range(n):
    if prices[i] < prices_m and goodness[i] > goodness_m:
        answer += 1

print(answer)


```



![image-20240307194444954](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240307194444954.png)



**27300: 模型整理**

http://cs101.openjudge.cn/practice/27300

（总是presentation error，找不出来，无奈抄了个答案）

##### 代码

```python
from collections import defaultdict

n = int(input())
d = defaultdict(list)
for _ in range(n):
    #name, para = input().strip().split('-')
    name, para = input().split('-')
    if para[-1]=='M':
        d[name].append((para, float(para[:-1])/1000) )
    else:
        d[name].append((para, float(para[:-1])))


sd = sorted(d)
#print(d)
for k in sd:
    paras = sorted(d[k],key=lambda x: x[1])
    #print(paras)
    value = ', '.join([i[0] for i in paras])
    print(f'{k}: {value}')
```



![image-20240307224612412](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240307224612412.png)





## 2. 学习总结和收获

本周做了一些选做，但是事情比较多所以做得比较少

感觉自己的码力较上学期有所下降，需要多练

本周周末准备系统学习树的写法，计划里事情还是很多，不知道能不能学完





