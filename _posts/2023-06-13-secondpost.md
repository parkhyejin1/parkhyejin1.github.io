---
layout : post
title : "SQLD"
excerpt: "SQLD 개념 정리"
categories: _Back-end,SQLD

tags : [developer, blog, git,Github,SQLD,SQL]

toc: true 
toc_sticky : true
comments : true
date : 2023-06-13
last_modified_at : 2023-06-13
---


**SQL**



-관계형 DB에서 데이터 정의, 조작, 제어를 위해 사용하는 언어

 
 

**SQL문장들의 종류**

-SQL은 여러가지 종류의 키워드 존재

-데이터의 집짓기, 데이터 조작, 조작한 데이터저장 /복구

-종류 :DDL/DML/DCL/TCL

 
 
 
 

**DML(Data Manioulation Language): 데이터 조작어**

-관계형 데이터베이스의 구조를 정의

Selete - 데이터 베이스안에 데이터 조회, 검색하기 위한 명령어 

Insert - 삽입

Update - 수정          

Delete - 삭제(사용자 Commit /로그 0 / 테이블 스키마 유지 - Rollback 가능)

> 데이터 베이스 테이블에 들어있는 데이터 변형 명령어 

ex)데이터를 테이블에 새로운 행 삽입, 원하지 않는 데이터삭제, 수정 하는것들의 명령어

 



**DDL(Data Definition Language) : 데이터 정의어**

-테이블에서 데이터를 입력, 수정, 삭제, 조회

Create - 생성

Alter - 변경

Drop -삭제(Autocommit/ 로그제거 / 모두제거)

Rename - 이름 변경 

 

> 테이블과 같은 구조를 정의하는데 사용되는 명령어

구조 생성, 변경, 삭제 ,이름변경 데이터 구조와 관련된 명령어

 
 

**DCL(Data Control Language) :데이터 제어어**

-데이터베이스 사용자에게 권한을 부여, 회수

Grant - DB접근,객체사용권한부여

Revoke - 회수

Truncate - 삭제( Autocommit/ 로그제거/ 테이블 스키마 유지 - 초기화 상태)

 

> 데이터베이스에 접근하고 객체들을 사용하고 권한을 주고, 회수하는 명령어 

 
 

**TCL(Transaction Control Language) : 트랜잭션 제어어**

-트랜잭션을 제어하는 명령어 

Commit 

Rollback 

Savepoint 

 

> 논리적인 작업 단위를 묶어 DML에 의해 조작된 결과를 작업단위(트랜잭션)별로 제어하는 명령어

 
 
 

**트랜잭션 (Transation): 데이터베이스 작업을 처리하는 단위**

-트랜잭션 특징 : 원자성 /일관성 / 고립성 / 지속성

원자성 : 연산 전부 실행  OR 전혀 실행 X (모 아니면 도)

일관성 : 실행전 이상 없을 시 이후에도 그대로 사용유지 (일관성 유지)

고립성 : 실행중 다른 트랜잭션 영향 받지 X 

지속성 : 영구적으로 반영되어 저장 0 
