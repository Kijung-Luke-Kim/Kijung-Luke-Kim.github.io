---
layout: post
title:  "Forager 모작(17) - 오늘할일"
date:   2020-10-11T09:00:00+0900
author: Kijung Luke Kim
categories: [Project, Forager]
tags: [game, forager]
image: /assets/img/posts/forager.jpg
---

## 1. 몬스터 (에니미 클래스) 수정
---
 
- 상속 관계 재정립
    
    - 스폰매니저 : 일정시간마다 다양한 형식으로 몬스터의 종류와 수가 스폰되는 알고리즘의 코드의 집합.
    - 유닛매니저 : 업데이트, 렌더, 추가, 삭제, 길찾기 알고리즘의 결과값을 푸시
    - 에너미 : 자신의 현재 타일 좌표와 이동경로 타일 인덱스를 가짐
    - 스컬 : A* 알고리즘 결과를 받아서 최적의 경로로 이동

- A* 길찾기 알고리즘 수정

    - 포리저 타일맵 클래스에 맞춰 코드 변경.

## 2. 발표 준비
---

> 깃 브랜치 머지 후 정리.
