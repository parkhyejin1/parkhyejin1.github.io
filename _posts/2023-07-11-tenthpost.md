---
layout : post
title : "MyBatis"
subtitle: "개념 정리"
excerpt: "Spring 개념 정리"
categories: _Spring

tags : [developer, blog, git,Github,jvm,java,gc,oop,mvc,CRUD,spring,mybatis]

toc: true 
toc_sticky : true
comments : true
date : 2023-07-11
last_modified_at : 2023-07-11
---

  <br/><br/> 
  
  **MyBatis란?**

 

> 객체 지향 언어인 자바의 관계형 데이터베이스 프로그래밍을 좀 더 쉽게 할 수 있게 도와 주는 개발 프레임 워크

 


   <br/><br/> 


 

**MyBatis특징**

 

- 복잡한 쿼리/ 다이나믹한 쿼리에 강함 

- 비슷한 쿼리는 남발 

- 프로그램 코드와 SQL쿼리 분리 코드의 간결성 및 유지보수 향상

- resultType, resultClass등 Vo를 사용하지 X, 조회결과를 사용자 정의 DTO, MAP 등으로 맵핑하여 사용0

- 빠른 개발이 가능, 생산성 향상 




   <br/><br/>
  

 

**Annotaion SQL작성**

 

> SQL활용 데이터 클래스와 테이블 생성

 

예시)
**
@Data
public class Student{
Private Long id;
Private String name;
Private Integer age;
Private String phone;
Private String email;
}**

>> Student.java

   <br/><br/>
 
**
INSERT INTO student(name,age,phone,email)
VALUES('hamzzi',2,'010-1212-7777','hamzzi@gmail.com');

INSERT INTO student(name,age,phone,email)
VALUES('Pig',4,'010-1212-7778','Pig@gmail.com');

INSERT INTO student(name,age,phone,email)
VALUES('gini',3,'010-1212-7747','gini@gmail.com');
**
>>dml.sql



 
  <br/><br/> 

  
 

**MyBatis @Mapper 활용 SQL 구문 실행**

 

 

- @Select / @ Insert/ @ Update /@Delete 선언 , 괄호 안 SQL 작성 

 

- 메소드 이름, 매개변수 선언 

   <br/><br/> 

**StudentMapper**

**
@Mapper

Public interface StudentMapper{

// insert
    @Insert("INSERT INTO students (name, age, phone, email)" +
            "VALUES (#{name}, #{age}, #{phone}, #{email})")
    void insertStudent(Student student);


// select
    @Select("SELECT * FROM students")
    List<Student> selectStudentAll();

  @Select("SELECT * FROM students WHERE id = #{id}")
  Student selectStudent(Long id);
    }

**
**

@Update("UPDATE students SET " +
        "name = #{name}, " +
        "age = #{age}," +
        "phone = #{phone}, " +
        "email = #{email] " 
        "WHERE id = #{id}")
void updateStudent(Student student);

@Delete("DELETE FROM students " +
        "WHERE id = #{id}")
void deleteStudent(Long id);
**

  <br/><br/> 

 **#{parameter}**

= 매개변수로 받아온 값 대입 


**
@Select("SELECT * FROM students WHERE id = #{id}")
Student selectStudent(Long id);

**

=> 매개변수로 받아온 id값, #{id} 대입
 

**#{} , ${}**

 

**#{}**

- 값에 '' 자동 삽입 

- PreparedStatement 통해 악의적인 쿼리주입을 예방

- 보안차원 유리

- 사용자의 입력 전달할때 사용 

   <br/><br/> 

**${}**

- 값에 '' 자동 Xx

- Statement 방법으로 파라매터가 출력 전달

- 의도적 쿼리주입 방어 Xx

- SQL injection 보안 위험 발생 0

- table 명 , column명 전달 할때 사용 

 

   <br/><br/>

  

**StuendtMapper 인터페이스에 만든 메소드 접근**

 

 

 **StudentDto.java**
**
@Repository
public class StudentDao {
    private final SqlSessionFactory sessionFactory;
    public StudentDao(SqlSessionFactory sessionFactory) {
        this.sessionFactory = sessionFactory;
    }
}
**
> sqlSessionFactory: 데이터베이스와 연결고 SQL 실행 모든것을 가진 객체

   <br/><br/> 

@Repository

public class StudentDao {

  public List<Student> readStudentAll() {
        try (SqlSession session = sessionFactory.openSession()) {
            StudentMapper studentMapper = session.getMapper(StudentMapper.class);
            return studentMapper.selectStudentAll();
        }
    }

   public void createStudent(Student student) {
        try (SqlSession session = sessionFactory.openSession()) {
            StudentMapper studentMapper = session.getMapper(StudentMapper.class);
            studentMapper.insertStudent(student);
        }
    }

  public Student readStudent(Long id) {
      try (SqlSession session = sessionFactory.openSession()) {
            StudentMapper studentMapper = session.getMapper(StudentMapper.class);
            return studentMapper.selectStudent(id);
        }
    }
}

> SqlSession : 핵심적 역할 객체 ,DB와 세션 나타냄

> session.getMapper(StudedntMapper.class) :  mapper 인터페이스 구현 클래스 얻음

> studentMapper.selectStudentAll : 구현 클래스 selectStudentAll 호출 

 

   <br/><br/> 

 

**XML SQL 작성**

 

- Mybatis에서 Mapper XML 파일을 이용, 데이터베이스와 상호작용 0 



   <br/><br/>

  

**Mapper XML 파일에 SQL 쿼리를 정의**

XML 파일은 데이터베이스와 매핑되는 SQL 문을 작성하는 데 사용

XML 파일에는 SQL 쿼리, 매개변수 매핑, 결과 매핑 등의 정보가 포함

 

   <br/><br/>
   
 

**StudentMapper.Xml**

```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<mapper namespace="com.example.mybatis.mapper.StudentXmlMapper">

    <select id="selectStudent" resultType="Student" parameterType="Long">
        SELECT * FROM students WHERE id = #{id};
    </select>

</mapper>```
 
```
<mapper namespace="com.example.mybatis.mapper.StudentXmlMapper"> 
...
</mapper>```


mapper 파일 root 요소 , namesapce 속성 포함 

namespace 속성은 mapper 파일과 연결된 Java 인터페이스의 경로를 지정

위의 코드에선 "com.example.mybatis.mapper.StudentXmlMapper"가 네임스페이스로 사용

 
```
<select id="selectStudent" resultType="Student" parameterType="Long">
        SELECT * FROM students WHERE id = #{id};
    </select>```


    
쿼리는 데이터를 조회하기 위한 SQL 쿼리를 정의하는 부분

id : SQL 쿼리의 고유 식별자입니다. Java 코드에서 해당 쿼리를 호출할 때 사용

resultType : SQL 쿼리의 실행 결과를 매핑할 Java 객체의 타입을 지정

parameterType : SQL 쿼리의 매개변수로 전달되는 Java 객체의 타입을 지정

 

 

 

MyBatis 구성 파일(yaml, properties …)에서 Mapper XML 파일의 위치를 지정하여

MyBatis가 해당 파일을 읽을 수 있도록 설정함 

 

**application.yaml**

```
spring:
  datasource:
    url: jdbc:sqlite:db.sqlite
    driver-class-name: org.sqlite.JDBC


mybatis:
  mapper-locations: "classpath:mybatis/mappers/*.xml"
  type-aliases-package: "com.example.mybatis.model"
  configuration:
    map-underscore-to-camel-case: true```

 ```   
mybatis:
  mapper-locations: "classpath:mybatis/mappers/*.xml"```
해당 부분이  클래스 경로에서 mybatis/mapper 디렉토리 아래에 있는 모든 XML 파일을 Mapper로 인식하도록 함.

SQL 문이 포함된 Mapper XML 파일을 사용, 데이터베이스와 상호작용

MyBatis는 XML 파일의 내용을 기반으로 SQL 문을 실행 , 결과 반환

 

 

StudentXmlMapper.java

import com.example.mybatis.model.Student;
import java.util.List;

public interface StudentXmlMapper {
    Student selectStudent(Long id);
}
MyBatis의 매퍼 인터페이스인 StudentXmlMapper.java 코드 

mapper xml 파일에서 id로 지정한 값과 같은 이름으로 메서드를 선언

Long 타입의 id 매개변수를 받아 특정 학생의 정보를 조회하는 역할

반환 타입으로는 Student 클래스를 사용
