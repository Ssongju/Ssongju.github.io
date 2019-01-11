---
layout: post
title: 전자정부프레임워크에서 workspace를 불러온 후 서버 구동시 에러 발생상황 해결 
date: 2019-01-11 11:05:00
tag: [전자정부프레임워크, Tomcat]
---
아주 오랜만의 포스팅이다. 그 동안의 공부를 게을리 한 것을 반성함과 다시 개발공부의 의지를 다지고자 하는 마음을 가지고 2019년 첫 포스팅을 시작한다.
###### 문제상황
  - 다른 PC의 workspaces를 통채로 복사 후 전자정부 프레임워크를 실행하여 프로젝트를 실행하려고 했으나 ClassNotFound 에러가 발생
 
###### 시도한 해결방법
  - 해결하고자 메이븐 업데이트를 돌렸으나 소용이 없었고, 
  - 클린 후 메이븐 업데이트를 돌려도 소용이 없었으며(반대로 해도)
  - 리퍼지토리를 삭제한 후 메이븐 업데이트를 했으나 소용없었다.
  - 서블릿 버전을 다른걸로 했으나 실패
~~~
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>javax.servlet-api</artifactId>
    <version>3.1.0</version>
    <scope>provided</scope>
</dependency>
~~~
  - 그래서 다시 다 지운 후, 워크스페이스를 불러오고 서버(톰캣)와 jre 경로를 재설정하고 서버를 디버깅 해보았다.
  - org.springframework.beans.factory.NoSuchBeanDefinitionException: No bean named 'springSecurityFilterChain' is defined 이 에러가 계속 나왔고, 이 에러명을 검색해보니~~~~ DB접속정보가 잘못되었을 거라는 내용이 있었다.
  - 그래서 global.properties(DB 접속정보 파일)을 확인해보니 디비 비밀번호가 잘못되어 있었고, 수정을 하고 서버를 다시 디버깅 해보느 정상적으로 동작하였다.
  - 구동시키겠다고 8시간정도는 지우고 설정하고 검색하는걸 반복해본듯 하다...