---
title: "[프로그래밍 언어] 파이썬 - Pandas"
author: Daekyo Jeong
date: 2021-04-14 19:00:00 +0900
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

## **Pandas 자주 사용하는 문법 정리**  


### Read  

```py
pd.read_csv(filePath, params)
```

자주 사용하는 params   

- sep = ','
- header = None (저장된 파일에 header가 따로 없을 때)

### write  

```py
pd.to_csv(filePath, params)
```

자주 사용하는 params  

- sep = ','  
- header = True  
- index = True  
- encoding = 'utf-8'  

<br/>
