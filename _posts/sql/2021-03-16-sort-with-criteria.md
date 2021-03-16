---
title:  "프로그래머스 Lv.1 - 여러 기준으로 정렬하기"
date:   2021-03-16 08:00:00 +0900
author: Kijung Luke Kim
categories: [SQL, Programmers]
tags: [select]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/59404

## 문제풀이
---

```sql
SELECT ANIMAL_ID, NAME, DATETIME
FROM ANIMAL_INS
ORDER BY NAME ASC, DATETIME DESC;
```