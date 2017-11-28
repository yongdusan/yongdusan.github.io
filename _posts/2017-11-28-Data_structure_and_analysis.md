---
layout: post 
title: "데이터 구조 및 분석" 
date: 2017-11-28 12:55:52 +0900 
categories: 
- 자료구조
tags:
- Object-oriented paradigm
- Software design
- UML
- Inheritance
---
Edwith - KAIST 문일철 교수 "데이터 구조및 분석" lecture note

### **Object-oriented paradigm and Software design**
#### S/W Design 과 Programming
- S/W Design cf. 설계도 (평면도) 
- Software Implementation (by Development) cf. 시공
Lobby 1, Lobby 2: Same role, Similar design and Different interior

#### 좋은 SW Design이란?
1. Correctness: 목적에 부합 & 에러 없음
2. Robustness:  예상되는 overloads, 오입력에 대해 error가 없음
3. Flexibility: 수정하기 용이함
4.  Usability and Re-usability: 사용자가 잘활용할수있도록 지원이 잘됨. 다른 목적/ 다른 환경에서도 사용하기 쉬움
5. Efficiency: 빠른 실행, 작은 크기, 구현이 쉬움

#### Object-Oriented Design
현실 세계의 개념을 추상화하여 SW로 나타내는 설계 방법
- Title (개념의 이름)
- Attribute (개념의 특성, 상태) - 정적
- Method (개념의 행동) - 동적

#### Class 와 Instance
1. Class (=conceptualization)
- 하나의 design 과 implementation 
2. Instance (=realization)
- 실행의 결과

#### Software Design as House Floorplan
- S/W design 은 건축 설계와 유사. 
즉, 마음대로 작성하는 것이 아니라 표준에 따라 작성됨
- S/W design 표준? UML (Unified Modeling Language)

#### UML Notation : Class and Instance
- Abstract class / Class
- Named instance / Unnamed instance

- Instance Name :: Class Name
- Attribute (Property, member variables) : 
  - +,#,- (name):(type)=(default value) (여기서 type은 input)
- Method (Member function)
  - +,#,- (name)(arguments):(type) (여기서 type은 return 하는 것)
- 참고: Visibility options 
  - +: public (통상 선호되는 방법)
  - #: protected
  - -: private
 
#### Encapsulation
- Object = Data (field, attribute) + Behavior (method, member function)
Data 변형은 Behavior 를 통해서만 
- 구현에 대한 책임 위임
- Utilizing the visibility
  - private: seen only within the class 
  - protected
  - public: everywhere
  - (*Encapsulation 하려면) method public -> data private
 - Python 은 visibility options 을 지원하지는 않음
 
#### Inheritance (상속)
- Inheritance : attribute (member variables, methods)를 descendants 에게 전달해줌 
- descendants는 new attribute를 가질수 있음
- descendants는 상속받은 attribute를 mask(무시)할 수 있음  
- 위 두 경우가 아닐 경우, 상속받은 attribute를 따름
- Python은 multiple inheritance 가능


