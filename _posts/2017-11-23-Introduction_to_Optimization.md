---

layout: post title: "영상이해를 위한 최적화 기법 Week01" date: 2017-11-23 15:18:52 +0900

categories: jekyll update
-------------------------

Week01 Introduction to Optimization

Lecture1. Introduction to Optimization

최적화: 여러 대안 중 최선을 뽑아내는 것 최적의 기준이 필요 수학적으로 세우면 비용함수 or 목적함수 비용함수를 바탕으로 비용을 최저로 만들어 주는 값 뽑아낼 수 있는 집합 feasible set 집합 내 원소 alternative

최적화는 일정 학문에 국한된 기법이 아님. 공학, 금융, 경제학 등 비롯 일상생활에서도 쓰임.

최적화의 동의어 Programming: 전략계획법. feasible set에서 최적을 뽑아내는 전략을 의미 Computer Programming과 구분하기 위해 Mathematical Programming 이라는 용어 사용

영상이해에서는 패턴 인식을 위해 확률론적으로 모델링을 많이함. 확률 분포에서 벌어질 확률을 최대화한다는 것은 지수 부분(Energy)을 최소화한다는 것과 같음.

비용함수 f(x) 중요한 것은 비용함수 f(x)를 최소화 하는 x의 값을 찾는 것! f(x)의 최소값이 아님

feasible set 을 먼저 정해줘야함. ex. 출근 시간을 가장 짧게 하는 기상 시간이 몇시인지가 중요.

<img scr ="https://files.slack.com/files-pri/T6PQ1PXMX-F84LR3YBE/001.png">

### Lecture2. History

(1) Linear Algebra(선형대수)의 태동 Optimization 기법 개발에 대한 motivation 기원전 고대 중국에서 선형 대수가 쓰임. - 역변환 기법 등

(2) 17~19C Gauss Least Square Estimation 가우스 소거법 행렬의 역변환 구하기 용이해짐 Lagrange dual 함수: 여러 제한 함수와 목적함수를 하나의 함수으로 만들수 있음 -> optimization 용이해짐

(3) Advent of numerical linear algebra (computer를 통한 근사화) - 1940년대 Computer의 등장, 세계1,2차 대전으로 인해 현실에서 풀어야할 문제들이 많이 생김 - 전략계획법의 발전 (군수품 운송 최적화 등) 이후 금융산업 등으로 전파 - 1970년대 다양한 Software의 등장 (FORTRAN 등) - Matlab, Scilab, Octave, R 등 (commodity technology 원리를 몰라도 사용 가능)

(4) Advent of linear and quardratic Programming - 1940년대 선형계획법의 발전 - 1950년대 금융 산업으로 전파 - 1960~70년대 비선형 목적함수 문제 해결 by 컴퓨터를 통한 수치 근사화

(5) Advent of convex Programming - 소련 등 서구권 비해 컴퓨팅 파워 부족, 이론적으로 파고들어가봄 (배경) - 최적화 문제를 어렵게 하는 원인? 목적함수가 선형 or 비선형 - 좀 더 연구해보니 linear 여부가 아니라 convexity - global minima를 쉽게 구할수 있나 없나

(6) Present - 통계학, 머신러닝, 이미지 프로세싱 등 여러산업에 사용

### Lecture3. Classification of optimization techniques in Computer Vision(1)

분류를 하는 것은 이해에 도움을 준다. (1) Classification of Optimization techniques 어떤 기준으로 분류할 것인지 영상이해에 있어서는 - feasible set의 성질에 따라 분류하는 것이 가장 기본적 - continuous, discrete, combinatorial and variable 최적화 4가지로 구분됨

A. "Discrete" (이산) vs "Continuous" (연속) 3차원 공간 상상 일정한 점을 둘러싸고 있는 구를 상상 구 내에 x 외에 들어있지 않다면 x는 isolated 구를 아무리 작게 만들어도 항상 x외 다른 점 y가 속해 있다면 x는 accumulated 점들이 다 isolated -> Discrete set 점들이 다 accumulated -> Continuous set

"Continuous optimization problems" 뒤에서 자세히 다룰것 "Discrete optimization problems" 크게 2가지로 분류 a. combinatorial optimization: 상대적으로 최근의 것. 숫자를 다루기 보다 객체를 다룬다고 보면 좋음. 객체가 isolated 되어 있기에 descrete optimization 으로 보기도 하고 별도의 optimization 으로 보기도 함. 조합 최적화 ex1. 3개의 pixel로 이뤄진 영상이 있다고 가정. pixel은 3가지 색으로 구성됨. 배경과 전경을 segmentation 하라는 문제가 주어짐 2^3 = 8 개의 조합이 가능. 이 중 비용함수를 최소화하는 조합을 찾는 것.

ex2. minimum spanning tree (MST, 최소신장트리) 여러 마을을 반드시 한번씩 거치면서 전선을 깔아야함 가장 전선을 최소화하는 방법

b. integer programming: LP relaxation이라고도 함. 연속형으로 가정하고 최적화 문제를 푸는 방법. 단점: 정확도가 떨어짐

<Graph Cuts optimization> segmentation 기법 흰쪽 b는 background, 검은쪽 o는 object 의미 이중 좌상단, 우하단 두 point는 사용자가 가장 확실한 pixel에 marking을 해준것. combination 방법 중 (c) 그림과 같이 Cut 하도록 비용함수를 설계해야됨.

Ex1. Graph cut based segmentation - 사용자 marking 하는 부분에 따라 segmentation 결과가 다름 (초기 설정의 중요성) - 4번째 grabcut: 전경, 배경 2가지 대신 1번만 해도 좋은 결과 얻을수 있음 - 5번째 세일리언트를 initial seed로 삼음. (사람 지정 불필요) (참고)세일리언트? 어디를 보는지

Ex2. Video Retargeting using graph Cuts 한 장의 영상을 시간의 흐름에 따라 겹겹이 쌓아주면 하나의 volume이 됨 volume에서 graph cut으로 왼쪽부분과 오른쪽부분. 가장 의미없다고 생각되는 부분을 뽑아내는 것 Retargeting

### Lecture4. Classification of optimization techniques in Computer Vision(2)

Variational Optimization (변분 최적화) Continous optimization 과 차이점 결과로 나오는 최적화 솔루션이 실수나 벡터가 아닌 함수(function)이 됨. 주어진 에너지 함수로부터 그것을 최적화하는 함수를 뽑아내는 것. (다른 말로는 이를 벡터로 표현하면 infinite dimensional한 값을 가짐)

ex. noise가 제거된 꺠끗한 영상 (신호함수) ex. shape를 잘 표현하는 curve 함수

-	functional: function 내 function. output은 반드시 real value로 나와야함

F가 functional y()라는 function을 가지고 있음 대부분 integral 적분형태로 나타남. (왜? real값을 output으로 주기 위함) 그 외에도 vector의 Norm (벡터의 크기) 등의 형태도 있음

f() 내에도 y(), y'()라는 함수를 가지고 있음. 그럼 f도 functional?? No. f는 real 값을 output으로 주지 못함.

Calculus of Variations 변수를 다루는 방법에서 더 나아가 함수를 다루는 영역 ex. P, Q 두 점을 잇는 curve의 길이를 구하는 function curve는 무한대 가능. curve의 길이를 최소화하는 curve는? 이러한 식으로 표현 가능. curve의 함수 y()

Euler-Lagrange Equation 을 이용해서 식을 변형 f를 구하고자하는 y로 미분 = f를 y'로 미분하고 그것을 변수인 x로 미분 ...계산하면 y의 2차 도함수가 0이 됨. 즉, y는 선형함수여야함.

Curve 함수 찾는 것 의료영상에서 자주 쓰임. 찾고자 하는 병변에 부합하는 지 (active contour model(snake)) level set: snake는 병변과 비병변을 구분하는 curve 함수를 노골적으로 찾는 것. (explicit representation) 이와 달리 병변 영역과 비병변 영역을 구분함으로써 두 영역 사이가 우리가 찾는 curve 함수가 됨 implicit representation zero 영역에 해당되는 점들을 이으면 curve function이 됨.

영상신호 함수를 찾는 것 Image denoising u를 함수가 아닌 변수로 보고 continuous 문제로 보기도 함. 즉, 이러한 구분이 무자르듯이 되는 것이 아니라 넘나들기도 한다.

그 외에도 비용함수의 linear 여부, convexity 여부로 분류하기도 함.
