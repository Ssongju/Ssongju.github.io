---
layout: post
title: "tomcat설치 설정과 tomcat 버전별 서블릿 스펙 헤맨것들"
date: 2018-07-16 16:27
tag: [jsp, servlet, HeadFirst servlet&jsp]
---
Head first servlet&jsp 교재로 공부하던 중 잘 안되거나 헤맨 부분들이다.

1. 환경변수 설정은 사용자 변수가 아닌 시스템 변수에서 해주자.
2. 톰캣 startup.bat이 바로 꺼지면 cmd창에서 실행해보자. 왜 안되는지 나온다.
3. 확인해본 결과 JAVA_HOME(C:\....\jdk), JRE_HOME(C:\....\jre) 변수가 없었다. 시스템 변수에 추가해주자.
4. 기본 루트는 webapps, 없으면 webapps/ROOT이다.
5. 서블릿 스펙은 2.4였다. 내가 쓴 것은 3.0
6. 톰캣 버전과 서블릿 몇버전을 지원하는지 확인하고 WEB-INF/web.xml을 작성하자

######Servlet2.2
~~~
<?xml version="1.0" encoding="UTF-8"?>```
<!DOCTYPE web-app PUBLIC "-//Sun Microsystems, Inc.//DTD Web Application 2.2//EN" "http://java.sun.com/j2ee/dtds/web-app_2_2.dtd">```
<web-app>
</web-app>
~~~

######Servlet2.3
~~~
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE web-app PUBLIC "-//Sun Microsystems, Inc.//DTD Web Application 2.3//EN" "http://java.sun.com/dtd/web-app_2_3.dtd">
<web-app>

</web-app>
~~~

######Servlet2.4
~~~
<?xml version="1.0" encoding="UTF-8"?>
<web-app id="servlet-2_4" version="2.4"
	xmlns="http://java.sun.com/xml/ns/j2ee"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://java.sun.com/xml/ns/j2ee http://java.sun.com/xml/ns/j2ee/web-app_2_4.xsd">

</web-app>
~~~

######Servlet2.5
~~~
<?xml version="1.0" encoding="UTF-8"?>
<web-app id="servlet-2_5" version="2.5"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xmlns="http://java.sun.com/xml/ns/javaee"
	xmlns:web="http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd"
	xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_2_5.xsd">

</web-app>
~~~

######Servlet3.0
~~~
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://java.sun.com/xml/ns/javaee"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://java.sun.com/xml/ns/javaee http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd"
	version="3.0">

</web-app>
~~~

######Servlet3.1
~~~
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd"
	version="3.1">

</web-app>
~~~

참고링크1. : [톰캣 버전별 서블릿 스펙](https://zetawiki.com/wiki/%ED%86%B0%EC%BA%A3_%EB%B2%84%EC%A0%84%EB%B3%84_%EC%84%9C%EB%B8%94%EB%A6%BF_%EC%8A%A4%ED%8E%99)

참고링크2. : [서블릿 버전별 DTD](http://antop.tistory.com/145)