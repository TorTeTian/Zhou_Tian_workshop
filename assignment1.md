# Assignment #1: 拉齐大家Python水平

Updated 0940 GMT+8 Feb 19, 2024

2024 spring, Complied by 周添 物理学院



**说明：**

1）数算课程的先修课是计概，由于计概学习中可能使用了不同的编程语言，而数算课程要求Python语言，因此第一周作业练习Python编程。如果有同学坚持使用C/C++，也可以，但是建议也要会Python语言。

2）请把每个题目解题思路（可选），源码Python, 或者C++（已经在Codeforces/Openjudge上AC），截图（包含Accepted），填写到下面作业模版中（推荐使用 typora https://typoraio.cn ，或者用word）。AC 或者没有AC，都请标上每个题目大致花费时间。

3）课程网站是Canvas平台, https://pku.instructure.com, 学校通知3月1日导入选课名单后启用。**作业写好后，保留在自己手中，待3月1日提交。**

提交时候先提交pdf文件，再把md或者doc文件上传到右侧“作业评论”。Canvas需要有同学清晰头像、提交文件有pdf、"作业评论"区有上传的md或者doc附件。

4）如果不能在截止前提交作业，请写明原因。



## 1. 题目

### 20742: 泰波拿契數

http://cs101.openjudge.cn/practice/20742/



思路：嘿嘿



##### 代码

```python
x = [0, 1, 1, 2, 4, 7, 13, 24, 44, 81, 149, 274, 504, 927, 1705, 3136, 5768, 10609, 19513, 35890, 66012, 121415, 223317, 410744, 755476, 1389537, 2555757, 4700770, 8646064, 15902591, 29249425, 53798080]

a = int(input())

print(x[a])

```



![image-20240220221246168](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240220221246168.png)





### 58A. Chat room

greedy/strings, 1000, http://codeforces.com/problemset/problem/58/A

##### 代码

```python
# Compiled by pku phy 2300011538

type_in = input()
pointer = 0
hello_letters=['h', 'e', 'l', 'l', 'o']

for i in range(len(type_in)):
    if pointer==5:
        break
    if type_in[i] == hello_letters[pointer]:
        pointer += 1

if pointer == 5:
    print('YES')
else:
    print('NO')


```

![image-20240220222152885](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240220222152885.png)





### 118A. String Task

implementation/strings, 1000, http://codeforces.com/problemset/problem/118/A



##### 代码

```python
# Compiled by pku phy zhou_tian 2300011538

def process(string):
    forbidden_letters = ['A', 'O', 'Y', 'E', 'U', 'I', 'a', 'o', 'y', 'e', 'u', 'i']
    result = ""
    for i in string:
        if not (i in forbidden_letters):
            result += "." + i.lower()
    print(result)


string = input()

process(string)


```



![image-20240220222321060](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240220222321060.png)





### 22359: Goldbach Conjecture

http://cs101.openjudge.cn/practice/22359/



##### 代码

```python
def is_prime(num):
    if num < 2:
        return False
    for i in range(2, int(num ** 0.5) + 1):
        if num % i == 0:
            return False
    return True


def find_primes_with_given_sum(target_sum):
    for i in range(2, target_sum):
        if is_prime(i) and is_prime(target_sum - i):
            return i, target_sum - i
    return None, None


target_sum = int(input())
prime_a, prime_b = find_primes_with_given_sum(target_sum)
print(prime_a, prime_b)

```

![image-20240220223520236](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240220223520236.png)



### 23563: 多项式时间复杂度

http://cs101.openjudge.cn/practice/23563/



##### 代码

```python
def i_eat_lemon(e):
    terms = e.split('+')
    max_e = 0

    for term in terms:
        coe, ex = term.split('n^')
        ex = int(ex)
        coe = int(coe) if coe else 1
        if ex > max_e and not coe == 0:
            max_e = ex

    if max_e == 0:
        return 'n^0'
    else:
        return 'n^{}'.format(max_e)


expression = input()
result = i_eat_lemon(expression)
print(result)

```



![image-20240220223633982](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240220223633982.png)





### 24684: 直播计票

http://cs101.openjudge.cn/practice/24684/

##### 代码

```python
from collections import defaultdict

nums = [int(i) for i in input().split()]
d = defaultdict(int)

for i in nums:
    d[i] += 1

maxi = 0
num_d = []

for key in d.keys():
    if d[key] > maxi:
        num_d = [key]
        maxi = d[key]
    elif d[key] == maxi:
        num_d.append(key)

num_d.sort()

for l in num_d:
    print(l, end=' ')

```



![image-20240220225725258](C:\Users\ukong\AppData\Roaming\Typora\typora-user-images\image-20240220225725258.png)

## 2. 学习总结和收获

2.20 白天断断续续地下雪 晚上连着下

开学好困，睡少了困，睡多了也困，没啥精气神。。。





