---
layout : post
title : "JAVA(1)"
subtitle: "개념 정리"
excerpt: "JAVA 개념 정리"
categories: _JAVA

tags : [developer, blog, git,Github,jvm,java,gc,oop]

toc: true 
toc_sticky : true
comments : true
date : 2023-06-20
last_modified_at : 2023-06-20
---



**JAVA란?**

 

 > 객체지향적 프로그래밍 언어 (OOP)

  ※객체지향적 언어 (OOP)란 : 프로그래밍에 사용될 데이터의 상태와 행위를 객체로 생성, 

     객체간 상호작용을 통해 비즈니스 로직 구성하는 프로그래밍 기법

 <br/><br/> 

**JAVA의 특징**

 

1.JVM이용하여 운영체제 독립적

2.객체지향언어- 캡슐화,상속, 다형성,추상화 특징

3.런타임식 데이터 타입이 결정되는 동적타입 언어

4.컴파일 언어와 인터프리터 언어 2가지 동작방식을 복합적으로 사용 , 하이브리드 언어라고 불리기도 함

5.GC 지원

  <br/><br/>

**JAVA 접근제어자**

 

> 클래스, 인터페이스, 멤버변수, 함수 등 접근을 제어하는 지시어

> 접근제어자로 인해 외부 객체의 무분별한 접근으로부터 내부 데이터 보호 (데이터 무결성)

|접근제어자|같은 클래스 멤버|	같은 패키지 멤버	|자식 클래스 멤버	|그외|
|-------|------------|----------------|-------------|---|
|Public	|0	|0	|0	|0|
|Protected|	0	|0	|0|	X|
|Default|0|	0|	X|	X|
|Private|	0|	X|	X|	X|


*public :  모든 패키지, 모든 클래스의 접근 허용

*protected  : 같은 패키지, 모든 클래스의 접근 허용 (단, 다른 패키지인 경우 자식 클래스의 접근 허용)

*default: 같은 패키지 내 클래스만 접근 허용

*private : 같은 클래스 내 접근만 허용

 <br/><br/>
 
**접근 제어자 사용 이유**

 

-객체지향프로그래밍이란 객체간 상호작용 코드로 표현하는것

-객체간 관계에 따라 접근할 수 있는것과 아닌것 ,권한 구분 필요 

-클래스 내부에 선언된 데이터 부적절한 사용으로부터 보호하기위해 사용 

  <br/><br/>

**JAVA final키워드** 

 

final이란 : 변수나 메소드 또는 클래스가 "변경 불가능" 하도록 만드는 자바 키워드

final 선언 시 , 무조건 초기화, 초기화 프로그램 실행 도중 수정 불가능 

  <br/><br/>

**final 사용 이유**

 

: 클래스, 메서드, 변수가 변하지 않도록 

  final 선언 시 절대 변하지 않는 값, 상수 가지게 됨

 데이터를 ReadOnly로 만들어, 객체내부 값의 변환이나 가공 하지 X선언, 데이터 지킬때 사용

  <br/><br/>

**인터페이스와 추상 클래스 차이**

 

-추상클래스 : abstract로 선언 되거나 추상메서드를 하나이상 포함한 클래스

 클래스이기 때문 하나만 상속 가능

 추상메소드 : 선언부만 있고, 구현부X 메소드, 하위 클래스에게 메소드의 구현 강제하는 메소드

 추상 클래스 ->extends 키워드 사용, 하나만 가능 

 

-인터페이스는 구현체 없이 메서드에 대한 명세만 가지고 있고, 모든 메서드 추상메서드 

 따라서 인터페이스를 상속받는 자식클래스에 모든 메서드에 대한 구현 강제, 다중상속 0

 인터페이스 -> implements 키워드 사용 ,여러개 

  <br/><br/>

**Overriding VS Overloading**

 

오버로딩

-같은 이름을 가진 메소드를 여러개 가지는것

-메소드의 이름은 같지만, 매개변수의 개수, 타입 등 다르게 함으로써, 같은 메소드의 이름을 다른 기능으로 재정의 사용

-메소드 이름 1개 여러개능 재정의 사용 = 가독성 좋음 

 

오버라이딩

-하위 클래스에서 상위클래스의 메소드를 재정의하여 사용

-상위 클래스 기능을 ,하위클래스에서 필요한 부분만 재 수정후 원하는 기능으로 구현

-오버라이딩 이점 : 코드 중복 줄이고, 기능확장 

 

>>오버라이딩과 오버로딩 모두 하나의 이름(기능)이 여러 구현을 할 수 있도록 해주는 객제지향의 다형성 특징 

 
 <br/><br/>
 

**JAVA Generic**

 
```py
 -<T> == Type
- <E> == Element
- <K> == Key
- <V> == Value
- <N> == Number
- <R> == Result
``` 

-컬렉션 사용시 볼 수 있음
-꺽쇠 <> 사용하여 타입 명시 = 컴파일 시 객체의 타입 체크
-의도하지 않은 타입의 객체가 저장되는것 제어, 잘못된 형변환 제어 = 안정성 높음
-동작은 같지만 클래스 타입만 바뀌어야하는 경우 쉽게 다룸 
 
```py
public class Main {
    public static void main(String[] args) {

        List<String> list = new ArrayList();
        Collection<String> collection = list;
    }
}
 
```

>> 위 collection , String type 명시 , String type 아닌 타입일 시, 컴파일 에러

  <br/><br/>

 

**Generic 장단점**

 

> 단점 : 제네닉 사용시 , 컴파일 시 타입 명시로인해 의도하지 않은 형변환 제어 

 

> 장점 :  타입만 변경해서 코드 수정해야할 경우 쉽게 변경 가능 

  <br/><br/>

**Static이란?**

 

> static 변수와 static 메소드, 즉 정적 멤버(=클래스 멤버)를 만들 수 있는 키워드 

 

-정적 필드와 정적 메소드는 인스턴스(객체) 아닌, 클래스에 고정 ,

 클래스 로더가 클래스를 로딩해 메모리 영역 적재할때,

 클래스 별로 관리되어 정적 메모리로 사용 0 

-객체 멤버는 객체를 생성 할때 Heap영역 할당 

  <br/><br/>

**Static 언제 사용 ?**

 

- 정적 멤버는 클래스가 메모리에 올라갈때 자동적으로 생성 , 객체 인스턴스 별도 생성 X 호출 하여 사용 

-Static은 유틸리티 함수를 만드는데 사용, 변하지 않는 자주 사용하는 값, 설정 정보등을 메모리에 올려, 객체 생성 비용 절감

 

  <br/><br/>

**Static 단점**

 

> 메모리에 올라가는것이므로 , 남용하여 메모리 낭비 0

 
 <br/><br/>
 

**JAVA main method  static 사용 이유**

 

> 메모리 초기화 후 객체 존재 X  객체멤버 메소드 바로 실행 X

> 객체 존재 여부 관계 X 쓰기위해 사용 , JVM 구동시 static 영역에 바로 배치

 <br/><br/>
 

**JVM**

> 자바 가상 머신 약자 (Java Virtual Machine) 컴퓨터가 자바 바이트 코드를 운영체제에 맞게 실행시키는 역할

> OS 종류 상관 X 자바 파일 실행 할수 있게 중개자 역할 , 플랫폼 독립적 특성

 
 <br/><br/>

**JVM 동작 과정**

프로그램이 실행되면 JVM은 OS로부터 필요한 메로리를 할당
자바 컴파일러(javac)가 자바 소스코드(.java)를 읽어들여 자바 바이트코드(.class)로 변환
Class Loader를 통해 Class 파일들을 JVM으로 로딩
로딩된 class 파일들은 Execution engine을 통해 해석
해석된 바이트코드는 Runtime Data Areas에 배치되어 실질적인 수행

<br/><br/> 


**JVM 구조**

> Class Loader, Exection engine, Runtime Data Area, Garbage Collector

![image](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fdwn4GP%2FbtrBQEnxXI5%2FYwktMYrsomqHZzWrscwZ11%2Fimg.png)

  <br/><br/>


-Class Loader는 자바 컴파일러가 .java 파일을 컴파일하여 .class 파일(바이트 코드)이 생성되면,
이 생성된 클래스 파일들을 엮어 Runtime Data Area 형태로 메모리에 적재하는 역할



-Execution Engine는 클래스 로더를 통해 JVM 내의 Runtime Data Area에 배치된 바이트 코드들을 명령어단위로 읽어서 실행. 메모리에 적재된 클래스들을 기계어로 변경해 명령어 단위로 실행하는 역할



-Garbage Collector는 Heap 메모리 영역에 생성 된 객체들 중에 참조되지 않는 객체들을 탐색 후 제거하는 역할



-Runtime Data Area는 JVM이 프로그램을 수행하기 위해 OS로 부터 별도로 할당 받은 메모리 공간


 
** - Runtime Data Area는 크게 5가지 영역으로 분배**


▶ 모든 스레드에서 공유하는 영역 

Method Area

-메소드 영역에서 자바 프로그램의 클래스 코드, 변수 코드, static, final 변수 등이 생성

 

Heap Area

-new 키워드로 생성한 객체가 저장되는 영역

-동적으로 생성된 객체와 배열이 저장되는 곳으로 Garbage Collection의 대상이 되는 영역

 

Stack Area

-지역 변수, 파라미터 등이 생성되는 영역, 동적으로 객체를 생성, 실제 객체는 Heap에 할당되고 해당 레퍼런스만 Stack에 저장

-Stack은 스레드별로 독자적

-Heap에 있는 객체가 Stack에서 참조 할 수 없는 경우 GC의 대상

 

▶ 각 스레드 별로 생성되는 영역

PC Register

-현재 쓰레드가 실행되는 부분의 주소와 명령을 저장하고 있다.(CPU의 PC Register와 다르다.)

 

Native Method

-자바외 언어로 작성된 네이티브 코드를 위한 메모리 영역

  <br/><br/>

**GC(Garbage Collector)**

> 가비지 컬렉터 : 힙, 메모리 관리르 위해 , 참조도고 있지 않는 객체들을 메모리에서 삭제

- 객체 = 힙 영역 저장 , 스택영역 = 주소값 저장 

- 힙영역에서 자신을 가르키는 주소값 X 시 참조되고 있지 X 판단

  <br/><br/>

**GC 동작 과정**

 

- 객체가 생성 되면 메모리를 Young 영역 저장 

- 객체 최초생성시 Young영역 Eden영역 위치

- Eden 영역에서 Minor GC 발생시 ,참조 중 객체는 1번 Survivor 영역으로 이동

- 1번 Survivor 영역에서 Minor GC 발생 시 , 참조 중 객체는 2번 Survivor 영역으로 이동,1번 Survivor  영역 비어있음

- Young 영역에서 오래 살아남은 객체 = Old 영역 이동

- Old 영역에 있는 객체는 Major GC 발생시 ,참조 여부에 따라 유지/ 삭제

 <br/><br/> 

**GC 알고리즘 종류**

 

1. Serial GC

 - 단순 방식

 - 싱글 스레드 동작, 느림

 - Mark-sweep-compact 알고리즘(mark하고, sweep(지우기)하고, compact(빈공간을 채워넣음)

 - 적은 메모리, CPU 코어 갯수 적을때 적합

 

2. Paraller GC

 - JAVA8 defualt GC

 - Serial GC와 알고리즘은 같지만 ,  GC를 처리하는 Thread가 여러개

 - 메모리, 코어 충분할때 적합

 

3. Paraller Old GC

 - Paraller GC는 Young영역에서만 멀티스레드를 사용

 - BUT 이건 Old 영역까지 멀티스레드를 사용

 - Paraller GC에서 Old GC 알고리즘을 개선한 버전

 
 <br/><br/>
 

**GC 장단점** 

 

장점 : 

- 메모리 누수 막을 수 0 

- 해체된 메모리에 접근하는 오류 , 해체된 메모리 한번 더 해체하는 이중해체 막을 수 0

 

단점 :

 - GC 메모리 해체 타이밍을 개발자가 정확하게 알기 어려움

 - 실시간성 강조되는 프로그램에 경우 GC에게 메모리 맡기는것 알맞지 X

 

 

 

 
