---
title:  "프로그래머스 Lv.1 - 역순 정렬하기"
date:   2021-03-10 08:00:00 +0900
author: Kijung Luke Kim
categories: [SQL, Programmers]
tags: [select]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/59035

## 문제풀이
---

```sql
SELECT NAME, DATETIME
FROM ANIMAL_INS
ORDER BY ANIMAL_ID DESC;
```