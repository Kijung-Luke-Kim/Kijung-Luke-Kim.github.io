---
layout: post
title:  "Forager 모작(19) - 오늘할일"
date:   2020-10-13T09:00:00+0900
author: Kijung Luke Kim
categories: [Project, Forager]
tags: [game, forager]
image: /assets/img/posts/forager.jpg
---

## 1. 몬스터 (에니미 클래스) AI 구현
---
 
- 이동 논리 구축
    
    - 스폰된 섬 안에서 이동을 제약
    - 공격 상태 아닌 경우 섬안에서 랜덤하게 움직이도록 한다.

- A* 길찾기 알고리즘 통합

    - 어제 작업한 길찾기 함수를 사용해 목표 좌표로의 이동을 처리.

## 2. 스폰매니저를 통한 던전 및 몬스터 생성  
---

- 토지구매를 통해 구입한 섬에서 랜덤하게 NPC와 몬스터가 생성되도록 수정.

- 마치 스타크래프트의 저그처럼, 단계적으로 평지 타일이 오염되도록 한다.

> 그동안 시뮬레이션적 요소에 집중하느라 신경쓰지 못했던 RPG 요소들을 추가