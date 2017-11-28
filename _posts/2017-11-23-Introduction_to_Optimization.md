---
layout: post 
title: "[Week 01] 영상이해를 위한 최적화 기법" 
date: 2017-11-23 15:18:52 +0900 
categories: 
- Image Understanding
tags:
- Optimization
- cost function
---

Edwith의 KAIST MOOC `영상이해를 위한 최적화 기법` (김창익 교수)

(Week01) Introduction to Optimization
-------------------------------------
![contents](/img/001.png)
### Lecture 1. Introduction to Optimization
#### 1. Optimization
-	Optimization (최적화): 여러 대안 중 최선을 뽑아내는 것.
-	최적을 판단? 기준이 필요! 이를 수학적으로 나타낸 것이 비용함수 (or 목적함수)  
-	feasible set: 비용을 최저로 만들어 주는 값을 뽑아낼 수 있는 집합
> Optimization 의 동의어 
> - Mathematical Programming (전략계획법)
> : feasible set 에서 최적을 뽑아내는 전략을 의미. 
> Computer Programming과 구분하기 위해 Mathematical Programming  
> - Energy Minimization (in Image Understanding)
> : 영상이해에서는 패턴 인식을 위해 확률론적으로 모델링을 많이함. 
> 확률 분포에서 일어날 확률을 최대화 = 지수 부분(Energy)을 최소화

#### 2. 비용 함수 f(x)
![fx](/img/003.png)
 - 비용함수 f(x)를 최소화 하는 x의 값을 찾는 것이 중요! f(x)의 최소값이 아님. 
 - 제약조건: feasible set(x의 집합) 을 정해주기 위함. 
  (ex. 출근 시간을 가장 짧게 하는 기상 시간이 몇시인지가 중요.)

### Lecture 2. History
#### 1. Linear Algebra(선형대수)의 태동
 - 선형대수: Optimization 기법 개발에 대한 motivation 
 - 기원전 고대 중국에서도 선형 대수가 쓰임.

#### 2. Optimization as a theoretical tool (17 ~ 19C) 
- Gauss: Least-Squares Estimation, 가우스 소거법 등 
![gauss](/img/004.png)
- Lagrange: Lagrangian 함수 
  - 여러 제한 조건과 목적 함수를 하나의 함수으로 만들수 있음 
  - optimization 용이해짐
![lagrangian](/img/005.png)
#### 3. Advent of numerical linear algebra (computer를 통한 근사화) 
- 1940년대 Computer의 등장 & 전쟁 인해 현실에서 풀어야할 문제 많아짐 
- 1970년대 이후 다양한 Software의 등장 (FORTRAN 등) 
이후 Matlab, Scilab, Octave, R 등으로 발전 
  (Commodity technology? 원리를 몰라도 사용 가능)

#### 4. Advent of linear and quadratic programming 
- 1940년대 LP(선형계획법)의 발전 (군사적 이유, ex. 최적의 군수품 수송 등)
- 1950년대 금융 산업으로 전파 (투자 risk 최소화) 
- 1960~70년대 비선형 목적함수 문제 해결 by 컴퓨터를 통한 수치 근사화

#### 5. Advent of convex Programming 
- 1980년대 소련 서구권 비해 컴퓨팅 파워 부족, 보다 이론적 접근 (배경) 
- 최적화 문제를 어렵게 하는 원인? 
-  (가정) 목적함수의 선형 여부? 
-  (결론) 선형 여부가 아니라 convexity가 좌우
     - convex problems are easy to get global minima
      
#### 6. Present 
- 통계학, 머신러닝, 이미지 프로세싱 등 여러산업에 사용

### Lecture 3. Classification of optimization techniques in Computer Vision(1)

어떤 주제에 대해 분류를 해보는 것은 이해하는데 도움이 된다.

#### 1. Classification of Optimization techniques
- 분류의 기준? 영상이해 분야에서는 feasible set의 성질에 따라 분류하는 것이 기본적 
- i) continuous, ii) discrete, iii) combinatorial and iv) variational 4가지로 구분됨

#### 2. "Discrete" (이산 최적화) Vs. "Continuous" (연속 최적화)
- 3차원 공간에 특정 점(x)를 둘러싸고 있는 구를 상상해보자. 
![ball](/img/006.png)
 - 구 안에 x 외에 다른 점이 없다면 x는 isolated point
     - 모든 점들이 isolated ? Discrete set
 - 구를 작게 만들어도, 항상 x 외 다른 점 y가 있다면 x는 accumulated point
     - 모든 점들이 accumulated? Continuous set


#### 3. Classification based on the nature of solution

 1. Continuous optimization problems: 추후 학습 예정
 2. Discrete optimization problems: 크게 2가지로 분류
	- combinatorial optimization (조합 최적화): 수치보다는 객체를 다룬다고 이해. 객체가 isolated 되어 있기에 discrete optimization 으로 보기도 하고 별도의 optmization으로 보기도 함.
	> (Ex 1) 영상 segmentation
  ![is](/img/007.png)
	> (Ex 2) MST(minimum spanning tree) 
  ![mst](/img/008.png)
	
	- integer programming: LP relaxation 또는 cutting plane method 라고도 함. 연속형으로 가정하고 최적화 문제를 푸는 방법. 정확도 떨어진다는 단점.
			
##### "Graph Cuts Optimization"
- Ex1. Graph cut based segmentation 
![Ex1](/img/009.png)
 : 사용자 marking 하는 부분에 따라 segmentation 결과가 다름 (초기 설정의 중요성) 
 - GrabCut: 전경, 배경 2가지 각각 지정하는 대신 1번만 해도 좋은 결과 얻을수 있음 
 - Markov Chain Embedded Graph Cuts: salient를 initial seed로 삼음. (사람 지정 불필요) 
     (*salient?* 어디를 보는지)

- Ex2. Video Re-targeting using graph Cuts 
![Ex2](/img/010.png)
: 한 장의 영상을 시간의 흐름에 따라 겹겹이 쌓아주면 하나의 volume이 됨.
 volume에서 graph cut으로 가장 의미없다고 생각되는 부분을 뽑아내는 것

### Lecture4. Classification of optimization techniques in Computer Vision(2)

##### 1. Variational Optimization (변분 최적화) 
- Continuous optimization 과 차이점? 결과로 나오는 최적화 솔루션이 실수나 벡터값이 아닌 함수. 즉, 주어진 에너지 함수로부터 그것을 최적화하는 함수를 뽑아내는 것. 
- 이를 벡터로 표현하면 infinite dimensional한 값을 가짐
> Ex. noise가 제거된 깨끗한 영상(신호함수) 
![Exe1]()
> Ex. shape를 잘 표현하는 curve 함수

##### 2. Calculus of Variations
![functional](/img/011.png)
-	functional: function 내 function. 단, output은 반드시 real value로 나와야함
- F는 functional으로 y라는 내부 function을 가지고 있음. 대부분 integral 적분형태로 나타남. (왜? real값을 output으로 주기 위함) 그 외에도 vector의 Norm (벡터의 크기) 등의 형태로 나타내기도 함
- f 내에도 y, y'라는 함수를 가지고 있음. f도 functional인가? 
  - No, 왜? f는 real 값을 output으로 주지 못함.

![curve](/img/012.png)
> Ex. P, Q 두 점을 잇는 curve의 길이를 구하는 function curve는 무한대 가능. 이 중 길이가 최소인 curve는? curve의 함수 y라 하고, Euler-Lagrange Equation 을 이용해서 식을 변형. f를 구하고자하는 y로 미분 = f를 y'로 미분하고 그것을 변수인 x로 미분. 이를 계산하면 y의 2차 도함수가 0이 됨. 즉, y는 선형함수(직선)여야함.
![1](/img/013.png)
![2](/img/014.png)

> Curve 함수 찾는 다른 예? 
![snake](/img/015.png)
> > 의료영상에서 자주 쓰임. (찾고자 하는 병변에 부합하는 지)
>  - active contour model(snake): 병변과 비병변을 구분하는 curve 함수를 노골적으로 찾는 것. (explicit representation) 
>  - level set: 이와 달리 병변 영역과 비병변 영역을 구분함으로써 두 영역 사이가 우리가 찾는 curve 함수가 됨 (implicit representation) zero 영역에 해당되는 점들을 이으면 curve 함수가 됨.
>> de-noising 처리
![denoise](/img/016.png) 
