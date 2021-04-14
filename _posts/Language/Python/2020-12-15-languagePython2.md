---
title: "[프로그래밍 언어] 파이썬 - 모듈"
author: Daekyo Jeong
date: 2020-12-15 20:00:00 +0900
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

# **queue**

파이썬은 queue 모듈을 통해 큐(Queue), 스택(Stack), 우선순위큐(PriorityQueue)를 제공한다.  

```py
import queue
```

## **Queue**

- **생성**  

```py
q = queue.Queue()
```

- **삽입**  

```py
q.put(item)
```

- **삭제**  

파이썬에서는 별도의 top() 함수를 제공하지 않는다.
get()을 통해 원소를 삭제하고 삭제한 원소를 반환한다.  

```py
item = q.get()
```

- **크기**  

```py
size = q.qsize()
```

<br/>

## **Stack**

- **생성**  

```py
q = queue.LifoQueue()
```

- **삽입**  

```py
q.put(item)
```

- **삭제**  

파이썬에서는 별도의 top() 함수를 제공하지 않는다.
get()을 통해 원소를 삭제하고 삭제한 원소를 반환한다.  

```py
item = q.get()
```

- **크기**  

```py
size = q.qsize()
```

<br/>

## **Priority Queue**

- **생성**  

```py
q = queue.PriorityQueue()
```

- **삽입**  

```py
q.put(item)
```

- **삭제**  

파이썬에서는 별도의 top() 함수를 제공하지 않는다.
get()을 통해 원소를 삭제하고 삭제한 원소를 반환한다.  

```py
item = q.get()
```

- **크기**  

```py
size = q.qsize()
```

<br/>
