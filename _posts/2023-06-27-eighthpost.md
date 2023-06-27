---
layout : post
title : "MVC 패턴"
subtitle: "개념 정리"
excerpt: "JAVA 개념 정리"
categories: _JAVA

tags : [developer, blog, git,Github,jvm,java,gc,oop,mvc]

toc: true 
toc_sticky : true
comments : true
date : 2023-06-27
last_modified_at : 2023-06-27
---



**MVC패턴이란?**

 

:Model -view-Controller 약자 

애플리케이션을 세가지 역할로 역할에 따라 세가지 모듈로 나눠 구분한 패턴



  <br/><br/> 

  

1.Model(모델) - 백그라운드에서 동작하는 비즈니스 로직(데이터)처리

 

: 어플리케이션 데이터, 모든 데이터 정보 가공, 수집하는 컴포넌트

  데이터를 가진 객체 

 

- 사용자가 이용하려는 모든 데이터를 가지고있어야함

- View (뷰) 나 Controller(컨트롤러)에 관한 정보 알수 X

- 변경 시 처리방법 구현 




  <br/><br/>


  

2.View(뷰) - 정보를 화면으로 보여줌

 

: 시각적 UI 요소

 클라이언트 측 기술은 HTML/CSS/Javascript들을 모와둔 컨테이너

 사용자가 볼 결과물을 생성하기 위해 모델로부터 정보를 얻음 

 

- Model이 가지고있는 데이터 저장 X

- Model 이나 Controller에 관한 정보 알면 X , 단순 표시 역할 

- 변경 시 처리방법 구현




  <br/><br/> 




3.Controller(컨트롤러) - 사용자 입력 처리, 흐름 제어 담당/Model과 View 연결

 

:Model과 View 연결 역할

사용자가 접근한 URL에 따라 사용자의 요청사항을 파악한 후 

요청에 맞는 데이터를 Model을 의뢰

데이터를 View에 반영해서 사용자에게 알려줌 

 

- Modle 또는 View 관한 정보 알아야 0 

- Model 또는 View 변경 인지 대처0



 
 <br/><br/> 
 



**MVC패턴 방식** 

 

: 모델 1/ 모델 2 방식 존재

 

- 모델 1 방식 : JSP에서 출력과 로직 전부 처리

- 모델 2 방식 : JSP에서 출력만 



 
 <br/><br/> 

 
 

**Model 1**

 

: Controller영역에 View 영역 같이 구현 방식 , 사용자 요청 전부 JSP 전부 처리

 요청받은 JSP는 Java Bean Service Class사용 웹브라우저 사용자가 요청한 작업처리, 결과 출력 


 

  <br/><br/> 


 

**Model 2**

 

: 웹브라우저 사용자의 요청을 서블릿이 받고, 서블릿은 해당요청을 View(보여준다)/Model(보낸다) 사용할지 판단 전송 

 HTML소스와 JAVA 소스 분리 = 모델1에 비해 확장 / 유지보수 용이 



 
 <br/><br/> 
 
 

 

|----|Model 1-------|Model 2--------------|
|----|--------------|--------------------| 
|장점|	빠르고 쉽게 개발 0 |	디자이너/ 개발자 분업 0 유지보수/확장 용이|                      
|단점 |	JSP파일 비대,Controller/View 혼재 이후 유지보수 어려움|설계어렵고, 개발 난이도 높음|


>>Model 1 방식 : 웹서비스 개발하는 경우 백엔드/프론트 역할 분담 모호 ,협업 쉽지 않아 실제 서비스 거의X



 

  <br/><br/> 



 

**MVC패턴 사용해야하는 이유는?**

 

- 비즈니스 로직과 UI로직 분리 : 유지보수 독릭적 수행0

 

- Model과 View가 다른 컴포넌트들에 종속되지 X : 애플리케이션의 확장성, 유연성에 유리

 

- 중복 코딩 문제 제거 
