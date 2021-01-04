---
title: "[프로그래머스 인공지능스쿨] Monthly Project 1"
author: Daekyo Jeong
date: 2021-01-07 00:00:00 +0900
categories: [강의, AI]
tags: [Programmers, AI, Python]

math: true
---

# **프로젝트 소개**   
<br/>

첫 번째 프로젝트는 데이터 분석 결과를 시각화하는 웹페이지를 개발하는 것이다.  

나는 그동안 배운 Python django를 이용하여 웹 어플리케이션을 개발할 것이다.  

## **주제 선정**

Kaggle에 있는 다양한 데이터들 중에 선정을 했다.  
둘러보던 중 OTT 서비스에 대한 데이터가 있길래 흥미로워서 이거로 선택했다.  
OTT 서비스 제공자(넷플릭스, Hulu, Prime Video, Dismey+)들을 비교해논 데이터이다.  

데이터 항목은 크게 영화에 대한 정보들과 어떤 OTT 플랫폼에서 제공되고 있는지가 있다.  

총 17가지의 속성이 있는데, 아마 내가 사용할 속성들은 다음과 같다.
영화 정보로 제목, 개봉년도, 시청나이제한, IMDb 평점, 장르 정도.  
4개의 OTT 플랫폼이 제공하고 있는지 체크하는 bool 값.

## **데이터 전처리 및 DB 저장**  

Django를 이용하면서 가장 편했던 것을 꼽으라면 아마 DB아닐까 싶다.  
따로 DB 연동도 필요없고, 파이썬을 이용해서 관리할 수 있다니, 신세계였다.  

우선 csv 파일에 있는 데이터들을 전처리해서 알맞게 DB에 넣어주어야 한다.  

위에서 사용할 데이터를 정하긴 했지만, 진행하다보면 어떻게 될지 모르기에 DB에는 모든 데이터를 가져오도록 했다.  

null 값도 제법 포함되어 있지만, 이에 대한 처리는 후에 진행할 것이고, 우선은 그대로의 데이터를 저장한다.  

여기서의 전처리는 데이터 타입만 알맞게 맞춰주도록 했다.  

예를 들어, csv 파일에 시청연령의 경우 x세 이상이면 x+로, 전체시청가능이면 all로 표기되어 있다.  
나는 INT 형을 윈하기에 +는 제거하고, all인 경우 0으로 바꾸어줬다.  

가장 고민했던 부분은 다중 속성을 가지는 항목들이었다.  

특히 장르는 꼭 사용할 생각이었는데, 장르에 다중 속성이 허용되어 있기에, 테이블을 추가로 만들어서 관리할지 고민했지만, 우선은 그대로 사용하기로 했다.  
추후 데이터 로딩 과정에서 ,로 분리하여 사용하는 식으로 설계할 예정이다.  

- django를 이용한 db 테이블 생성  

```py
from django.db import models

# Create your models here.
class OTT(models.Model):
    def __str__(self):
        return self.title
    id = models.IntegerField(primary_key=True)
    title = models.CharField(default="",max_length=120)
    year = models.IntegerField(default=0)
    age = models.IntegerField(default=0, null=True, blank=True)
    imdb = models.FloatField(default=0, null=True, blank=True)
    rotten_tomatoes = models.FloatField(default=0, null=True, blank=True)
    netflix = models.BooleanField(default=False)
    hulu = models.BooleanField(default=False)
    primevideo = models.BooleanField(default=False)
    disneyplus = models.BooleanField(default=False)
    directors = models.CharField(default="",max_length=500, null=True, blank=True)
    genres = models.CharField(default="",max_length=100, null=True, blank=True)
    country = models.CharField(default="",max_length=300, null=True, blank=True)
    language = models.CharField(default="",max_length=100, null=True, blank=True)
    runtime = models.FloatField(default=0, null=True, blank=True)
```

- 데이터 전처리 및 DB 저장  

```py
from .models import OTT
import pandas as pd
import numpy as np
def init():
    ott_data = pd.read_csv("./data/MoviesOnStreamingPlatforms_updated.csv")
    cnt = 0
    for i in range(len(ott_data)):
        item = ott_data.iloc[i]
        id = int(item['ID'])
        title = checkNull('Title', item, 'str')
        year = checkNull('Year', item, 'int')
        if item.isnull()['Age']:
            age = None
        else:
            age = item['Age']
            if age == 'all':
                age = 0
            else:
                age = age[:-1]
            age = int(age)
        imdb = checkNull('IMDb', item, 'float')

        if item.isnull()['Rotten Tomatoes']:
            rottenTomatoes = None
        else:
            rottenTomatoes = item['Rotten Tomatoes']
            rottenTomatoes = rottenTomatoes[:-1]
            rottenTomatoes = float(rottenTomatoes) * 0.01
        netflix = checkNull('Netflix', item, 'bool')
        hulu = checkNull('Hulu', item, 'bool')
        primevideo = checkNull('Prime Video', item, 'bool')
        disneyplus = checkNull('Disney+', item, 'bool')
        directors = checkNull('Directors', item, 'str')
        genres = checkNull('Genres', item, 'str')
        country = checkNull('Country', item, 'str')
        language = checkNull('Language', item, 'str')
        runtime = checkNull('Runtime', item, 'int')
        data = OTT(id = id, title = title, year = year, age = age, imdb = imdb, rotten_tomatoes = rottenTomatoes, netflix = netflix, hulu = hulu, primevideo = primevideo, disneyplus = disneyplus, directors = directors, genres = genres, country = country, language = language, runtime = runtime)
        data.save()
        cnt += 1
    return cnt

def checkNull(name, item, dtype):
    if item.isnull()[name]:
        return None
    else:
        if dtype == 'str':
            return str(item[name])
        elif dtype == 'int':
            return int(item[name])
        elif dtype == 'float':
            return float(item[name])
        elif dtype == 'bool':
            return bool(item[name])

```

## **웹 페이지 만들기**  



<br/>
