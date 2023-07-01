---
layout : post
title : "CRUD"
subtitle: "개념 정리"
excerpt: "Spring 개념 정리"
categories: _Spring

tags : [developer, blog, git,Github,jvm,java,gc,oop,mvc,CRUD,spring]

toc: true 
toc_sticky : true
comments : true
date : 2023-07-02
last_modified_at : 2023-07-02
---

  <br/><br/> 

  
**CRUD란?**

 

>데이터 처리 기능 

: Create생성/Read읽기/Update갱신/Delete삭제



 
  <br/><br/> 
 


데이터베이스 : 기초적 4가지 쿼리형식 의미

|| 	조작|	SQL|
|-----|-----|-------|
|Create|생성|INSERT|
|Read	|조회|SELECT|
|Update|수정|UPDATE|
|Delete|삭제|DELETE|


 

   <br/><br/> 



클라이언트 - 서버간 HTTP프로토콜 사용, RESTful하게 데이터전송

|| 	조작|	Method|
|------|-----|------|
|Create|생성|POST|
|Read	|읽기|GET|
|Update|갱신|PUT|
|Delete|삭제|DELETE|

  <br/><br/> 
  
Create =POST 

:create는 서버에 정보를 올려달라는 요청

 POSST통해 URL요청하면 리소스 생성

   <br/><br/> 

Read =GET

:read는 서버에서 정보를 불러오는 요청 

 GET을 통해 해당 리소스 조회 후  해당 도큐먼트에 대한 자세한 정보를 가져옴

   <br/><br/> 

Update =PUT

:update는 정보 바꾸는 요청

   <br/><br/> 

Delete =DELETE

:delete는 정보 지우는 요청 

 DELETE통해 리소스 삭제 가능 



 
  <br/><br/> 


 

**JSON**

 

:서버에서 클라이언트로 데이터를 보낼때 json양식 사용 전달

  <br/><br/> 

```
{
key       Value
"name" : "햄찌",
"age"  : "1"
}```
