
---
layout: post 
title: "Google Cloud Dataprep" 
date: 2017-12-19 12:55:52 +0900 
categories: 
- GCP
tags:
- Cloud Dataprep

---

## Google Cloud Dataprep

Google과 Trifacta (Data wangling 업체) 가 콜라보로 만든 데이터 전처리 제품 
- 2017년 3월 Google Cloud Next Conference 에서 처음 공개
- 2017년 9월 Beta version 공개

-------------------------------
#### 일단 전처리란 무엇인가?

데이터 분석을 하기 위해서는 다양한 소스로부터 데이터를 추출, **추출된 raw data를 변환/가공**하여 적재하는 과정 [(ETL)](https://en.wikipedia.org/wiki/Extract,_transform,_load) 이 필요

![image](https://blogs-images.forbes.com/gilpress/files/2016/03/Time-1200x511.jpg?width=960)
분석할 때 약 80%의 시간을 전처리에 사용. 

![image2](https://blogs-images.forbes.com/gilpress/files/2016/03/Least-Enjoyable4-1200x511.jpg?width=960)
76%가 업무 중 가장 노잼인 과정을 전처리라고 함

결론: 전처리는 노잼 & 시간 많이듬 (=노가다) 
빠르고, 쉽게 할 수 없을까 하는 Needs에서 시작.
[(Fobes)](https://www.forbes.com/sites/gilpress/2016/03/23/data-preparation-most-time-consuming-least-enjoyable-data-science-task-survey-says/#63b5f31f6f63)

------------------
#### 다른 전처리 툴과 차이?

Trifacta Wrangler 
: 100MB 이하만 무료

OpenRefine (오픈소스) 
: Wrangler 대비 구림


당연하지만 Google Cloud 와 연동 (BigQuery, DataStorage)
& 사용하기 쉬움. (coding 에 익숙하지 않아도)

(참고: AWS에는 Glue와 유사하다고 함)

기타 특장점은 [여기서](https://cloud.google.com/dataprep/) 확인

