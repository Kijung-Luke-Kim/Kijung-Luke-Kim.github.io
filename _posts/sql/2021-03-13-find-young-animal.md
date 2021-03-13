---
title:  "프로그래머스 Lv.1 - 어린 동물 찾기"
date:   2021-03-13 08:00:00 +0900
author: Kijung Luke Kim
categories: [SQL, Programmers]
tags: [select]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/59037

## 문제풀이
---

```sql
SELECT ANIMAL_ID, NAME
FROM ANIMAL_INS
WHERE INTAKE_CONDITION != 'Aged'
ORDER BY ANIMAL_ID;
```