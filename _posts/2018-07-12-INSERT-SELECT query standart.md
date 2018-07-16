---
layout: post
title: "INSERT-SELECT 쿼리 표준"
date: 2018-07-12 16:08
tag: slq, query
---
SELECT문으로 조회한 데이트를 INSERT 할 때, 
INSERT INTO test1 VALUE(SELECT aa, bb FROM test2 WHERE dd = 'dd');
이렇게 쓰지 말고

INSERT INTO test1 (aa, bb)
SELECT aa, dd FROM test2 WHERE dd = 'dd'
이렇게 쓰자. VALUE안에 자료에 SELECT문을 넣는것은 쿼리 표준이 아니기 때문이다.

[참고링크](http://okky.kr/article/236619)