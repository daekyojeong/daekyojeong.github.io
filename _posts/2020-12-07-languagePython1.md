---
title: "[프로그래밍 언어] 파이썬 - 자료 구조"
author: Daekyo Jeong
date: 2020-12-07 23:00:00 +0900
categories: [프로그래밍 언어, Python]
tags: [Programming, Language, Python]
---

---
**Contents**

{:.no_toc}

* Will be replaced with the ToC, excluding the "Contents" header
{:toc}
---

<br/>

# **자료 구조**

## **줄 결합**

\ 를 사용하여 명시적으로 두 개 이상의 라인을 결합할 수 있다.   
[], {}, () 가 사용되는 경우 \ 없이 줄을 나눠도 된다.   
```py
if x > 100 and y > 100 \
  and z > 100 and k > 100 \
  and i > 100:
   res = 100

a = [1,2,3,4,5
     6,7,8,9,10]
```
## **문자열**

- **문자열 연산**

```py
a = 'p'
b = 'y'
c = a + b
# c = 'py'

c = a * 2
# c = 'pp'
```

- **길이 구하기**  

```py
a = 'abcd'
l = len(a)
# l = 4
```

- **슬라이싱**  

```py
a[x:y]
# x <= a < y
a[x:]
# x <= a < len(a)
a[:y]
# 0 <= a < y
a[:]
# 0 <= a < len(a)
```

- **count**

```py
#문자 개수 세기
a = "apple"
a.count("p")
# 2
```

- **find**

```py
#위치 찾기
a = "apple"
a.find("p")
#1
#처음 나오는 위치 반환
#존재하지 않는다면 -1 반환
```

- **join**

```py
str = "abc"
",".join(str)
# "a,b,c"
```

- **대,소문자 변환**

```py
a = 'hi'
a.upper()
# 'HI'
a.lower()
# 'hi'
```

- **split**

```py
a = "a b c"
a.split()
# a = ['a', 'b', 'c']
a = "a,b,c"
a.split(',')
# a = ['a', 'b', 'c']
```
<br/>

## **List**
- **생성**

```py
a = []
# a = []
a = [1,2]
# a = [1,2]
```

- **연산**

```py
a = [1,2,3]
b = [4,5,6]
a + b
# [1,2,3,4,5,6]
a * 3
# [1,2,3,1,2,3,1,2,3]
```

- **길이구하기**

```py
a = [1,2,3]
len(a)
# 3
```

- **요소 삭제**

```py
a = [1,2,3]
del a[1]
# a = [1,3]
a.remove(3)
# a = [1,2]
# remove(item)
# 첫 번째로 나오는 item 삭제
a.pop()
# a = [1,2]
# pop(index)
# index 위치의 원소를 삭제하고 값을 반환
# index를 비워두면 가장 마지막 원소를 삭제하고 반환
```

- **요소 추가**

```py
a = [1,2,3]
a.append(4)
# a = [1,2,3,4]
a.insert(1, 4)
# a = [1,4,2,3]
# insert(index,value)
```

- **슬라이싱**

```py
a[x:y]
# x <= a < y
a[x:]
# x <= a < len(a)
a[:y]
# 0 <= a < y
a[:]
# 0 <= a < len(a)
```

- **복사**

```py
a = [1,2,3]
b = a[:]
```

- **정렬**

```py
a = [1,3,2]
a.sort()
# a = [1,2,3]
```

- **뒤집기**

```py
a = [1,2,3]
a.reverse()
# a = [3,2,1]
```

- **검색**

```py
a = [1,2,3]
a.index(3)
# 2
a.index(1)
# 0
```

- **count**

```py
a = [1,2,3,1]
a.count(1)
# 2
```

- **확장**

```py
a = [1,2,3]
b = [4,5]
a.extend(b)
# a = [1,2,3,4,5]
a += b
# a = [1,2,3,4,5]
```
<br/>

## **Tuple**

값의 변경이 불가능하다는 점을 제외하면 리스트와 동일   
튜플의 요소는 한번 지정하면 지우거나 변경이 불가능  


- **생성**

```py
t1 = ()
t2 = (1,2)
t3 = 1,2
```

- **연산**

```py
t1 = (1,2)
t2 = (3,4)
t1 + t2
# (1,2,3,4)
t1 * 3
# (1,2,1,2,1,2)
```
<br/>

## **Dictionary**   
key 값에는 변하는 값을 쓸 수 없음  
> ex) list 사용불가, tuple은 사용가능  

- **생성**

```py
dic1 = {}
dic2 = {1:'a', 2:'b'}
# {key1:value1, key2:value2, ...}
```

- **추가**

```py
dic = {1:'a'}
dic[2] = 'b'
# dic = {1:'a', 2:'b'}
```

- **제거**

```py
dic = {1:'a', 2:'b'}
del dic[1]
# dic = {1:'a'}
```

- **키 사용하기**

```py
dic = {1:'a', 2:'b'}
dic[1]
dic.get(1)
# 'a'
dic = {'a':'apple', 'b':'banana'}
dic['a']
dic.get('a')
# 'apple'
```

[] 를 사용하면 존재하지 않는 키를 가져올 경우 오류 발생,  
get() 을 사용하면 None 반환  
key 값이 없는 경우 default 값을 반환하게 할 수 있다.   
`a.get(key, default)` 와 같이 사용하면 된다.  

- **리스트 만들기**

```py
dic = {1:'a', 2:'b', 3:'c', 4:'d'}
dic.key()
# key List
# [1,2,3,4]
dic.values()
# value List
# ['a','b','c','d']
dic.items()
# key, value List
# [(1, 'a'), (2, 'b'), (3, 'c'), (4, 'd')]
```

세 가지 모두 수행 결과로 리스트를 얻지만, 기본 리스트의 append, insert, pop, remove, sort 함수는 수행할 수 없음  
이 경우 `list(dic.key())` 를 이용해 리스트로 변환하여 사용하면 됨  

- **Key 검사**

```py
dic = {1:'a',2:'b',3:'c'}
1 in dic
# True
5 in dic
# False
```

<br/>

## **Set**

집합은 중복을 허용하지 않고, 순서가 없다.  

- **생성**

```py
s1 = set([1,2,3])
# s1 = {1,2,3}
s1 = set("hello")
# s1 = {'e', 'h', 'l', 'o'}
```

- **값에 접근**

```py
s1 = set([1,2,3])
l1 = list(s1)
l1[0]
# 1
t1 = tuple(s1)
t1[0]
# 1
```

- **집합 연산**

```py
s1 = set([1,2,3,4])
s2 = set([3,4,5,6])

# 교집합
s1 & s2
s1.intersection(s2)
s2.intersection(s1)
# {3,4}

# 합집합
s1 | s2
s1.union(s2)
s2.union(s1)
# {1,2,3,4,5,6}

# 차집합
s1 - s2
s1.difference(s2)
# {1,2}
s2 - s1
s2.difference(s1)
# {5,6}
```

- **추가**

```py
s1 = set([1,2,3])
s1.add(4)
# s1 = {1,2,3,4}
s1.update([3,4,5])
# s1 = {1,2,3,4,5}
```

- **제거**

```py
s1 = set([1,2,3])
s1.remove(2)
# s1 = {1,3}
```
