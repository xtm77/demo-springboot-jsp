# Spring Boot JSP

## JSP 의존성 라이브러리 추가
### Maven 의존성 라이브러리 추가
- 버전은 parent의 버전을 상속 받을 경우 생략
```xml
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>jstl</artifactId>
    <!--<version>1.2</version>-->
</dependency>
<dependency>
    <groupId>org.apache.tomcat.embed</groupId>
    <artifactId>tomcat-embed-jasper</artifactId>
    <!--<version>9.0.21</version>-->
</dependency>
```

## webapp/WEB-INF 디렉토리 생성
### jsp 파일을 놓을 디렉토리를 생성
- src/main/webapp/WEB-INF 디렉토리를 생성 (* src/main/resources/templates 에서는 동작하지 않는다.)
### sample.jsp 생성
```html
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8" %>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<!DOCTYPE html>
<html lang="ko">
<head>
    <title>mr::demo::sample</title>
</head>
<body>
sample
</body>
</html>
```

## application.properties에 jsp 파일 위치와 확장자 설정
```properties
spring.mvc.view.prefix=/WEB-INF/
spring.mvc.view.suffix=.jsp
```

## Controller 추가
```java
package com.mysticracoon.demo;

import org.springframework.stereotype.Controller;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;

@Controller
@RequestMapping("")
public class DefaultController {

    @GetMapping("/")
    public String sample() {
        return "sample";
    }
}
```
