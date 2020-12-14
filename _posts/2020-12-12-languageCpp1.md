---
title: "[프로그래밍 언어] C++ - STL 정리"
author: Daekyo Jeong
date: 2020-12-12 23:00:00 +0900
categories: [프로그래밍 언어, Cpp]
tags: [Programming, Language, Cpp]
---

---
**Contents**

{:.no_toc}

* Will be replaced with the ToC, excluding the "Contents" header
{:toc}
---

<br/>

# **STL(Standard Template Library)**

## **Vector**

배열과 거의 비슷하지만, 메모리를 잡아주지 않아도 된다.  
배열 동적할당의 상위버전이랄까  

- **header**  

```cpp
#include <vector>
```

- **생성**

```cpp
vector<int> v1;
// 빈 벡터 생성
vector<int> v2(3);
// default값 0으로 초기화된 크기 3의 벡터
// v2 = [0,0,0]
vector<int> v3(3,1);
// 1로 초기화된 크기 3의 벡터
// v3 = [1,1,1]
vector<int> v4(v3);
// v3를 복사해서 생성
// v4 = [1,1,1]
```

- **assign**

```cpp
v.assign(5,2);
// v = [2,2,2,2,2]
```

- **원소 참조**

```cpp
v.at(index);
v[index];
// index의 원소를 참조
v.front();
// 첫 번째 원소 참조
v.back();
// 마지막 원소 참조
```

- **원소 추가**

```cpp
v.push_back(item);
// 마지막 원소 뒤에 item 삽입

v.insert(index, item);
// index 위치에 item 삽입
// 삽입한 곳의 iterator 반환

v.insert(index, count, item);
// index 위치에 count 개수만큼 item 삽입
```

- **원소 제거**

```cpp
v.clear();
//모든 원소 제거
v.pop_back();
// 마지막 원소를 제거
v.erase(iterator);
//iterator가 위치한 원소를 제거
```

- **크기 연산**

```cpp
v.size();
//원소의 개수를 반환
v.empty()
// size가 0이면 true 반환
```

<br/>

## **Stack**  

- **header**  

```cpp
#include <stack>
```

- **생성**

```cpp
stack<int> st;
```

- **추가**

```cpp
st.push(item);
// item 삽입
```

- **제거**

```cpp
st.pop();
// top이 가르키는 원소 제거
```

- **값 읽기**

```cpp
st.top();
// 가장 위에 있는 원소 반환
```

- **원소 개수**

```cpp
st.size();
//원소 개수 반환
st.empty();
//비어있으면 true 반환
```

<br/>


## **Queue**  

- **header**  

```cpp
#include <queue>
```

- **생성**

```cpp
queue<int> q;
```

- **추가**

```cpp
q.push(item);
// item 삽입
```

- **제거**

```cpp
q.pop();
// 가장 앞의 원소 제거
```

- **값 읽기**

```cpp
q.front();
// 가장 앞에 있는 원소 반환
```

- **원소 개수**

```cpp
q.size();
//원소 개수 반환
q.empty();
//비어있으면 true 반환
```

<br/>

## **Priority Queue**  

- **header**  

```cpp
#include <queue>
```

- **생성**

```cpp
priority_queue<int> pq;
//내림차순 less<> 기반
priority_queue<int, vector<int>, greater<int>> pq;
//오름차순 기반
priority_queue<int, vector<int>, cmp> pq;
//사용자 지정 정렬 기준으로 생성 가능  
//cmd는 따로 구현
```

- **추가**

```cpp
pq.push(item);
// item 삽입
```

- **제거**

```cpp
pq.pop();
// top이 가르키는 원소 제거
```

- **값 읽기**

```cpp
pq.top();
// 가장 위에 있는 원소 반환
```

- **원소 개수**

```cpp
pq.size();
//원소 개수 반환
pq.empty();
//비어있으면 true 반환
```

<br/>

## **Deque**  

- **header**  

```cpp
#include <deque>
```

- **생성**

```cpp
deque<int> dq;
```

- **추가**

```cpp
dq.push_front(item);
// 첫 번째 원소 앞에 item 삽입
dq.push_back(item);
// 마지막 원소 뒤에 item 삽입
dq.insert(index, item);
// index 위치에 item 삽입
dq.insert(index, count, item);
// index 위치에 item을 count번 삽입
```

- **제거**

```cpp
dq.pop_front();
// 첫 번째 원소 제거
dq.pop_back();
// 마지막 원소 제거
dq.clear();
// 모든 원소 제거
dq.erase(iterator);
//iterator가 가르키는 원소 제거
```

- **값 읽기**

```cpp
dq.at(index);
dq[index];
// index 번째 원소 참조
dq.front();
// 첫 번째 원소 참조
dq.back();
// 마지막 원소 참조
```

- **원소 개수**

```cpp
dq.size();
//원소 개수 반환
dq.empty();
//비어있으면 true 반환
```

<br/>
