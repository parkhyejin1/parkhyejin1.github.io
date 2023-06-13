---
layout : post
title : "Constraint 제약조건"
subtitle: "개념 정리"
excerpt: "SQLD 개념 정리"
categories: _SQLD

tags : [developer, blog, git,Github,SQLD,SQL]

toc: true 
toc_sticky : true
comments : true
date : 2023-06-14
last_modified_at : 2023-06-14
---




**Constraint 제약조건**

- 데이터 무결성을 유지하기 위한 방법

 <br/><br/>

**제약조건 종류**

- PK/ Unique / NOTNULL / Check / FK

 <br/><br/>

**Primary Key (기본키)**

- 기본키 제약 = 고유키 제약 & NOTNULL

- 한테이블에 하나만 지정 가능 

- NULL값 입력 X 

- 중복 불가 

 <br/><br/>

**Unique (고유키)**

- 테이블 저장된 행 데이터를 고유하게 식별하기 위한 고유키 정의 

- 중복 불가 ( NULL끼리는 중복으로 간주 X) 

- NULL가능 

 <br/><br/>

**NOTNULL**

- NULL값 입력 금지

- 중복 가능 

 <br/><br/>

**Check**

- 입력 할 수 있는 값의 범위 제한 

- 논리식으로 지정 (True/ False로 평가 )

- 설정을 조건식으로 만족하는 데이터만 입력 가능 

-조건식을 만족하지 않는 데이터는 입력 거부

 <br/><br/>

**Foreign Key( 외래키)**

- 외래키 지정시 참조 무결성 제약 옵션 선택 가능

- 관계형 데이터베이스에서 테이블 간의 관계 정의하기 위해   기본키를 다른 테이블의 외래키로 복사하는 경우 생성 

- 다른 테이블 열을 참조하여 해당 테이블 존재하는 값만 입력 가능 

- 다른 테이블 고유키 참조 

- NULL가능 

- 한테이블에 여러개 0

- 참조 무결성 제약 0

 

 

 

 
