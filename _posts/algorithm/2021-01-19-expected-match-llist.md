---
title:  "프로그래머스 Lv.2 - 예상 대진표"
date:   2021-01-19 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [teamstown]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12985

## 문제풀이
---

```cpp
#include <iostream>
#define ABS(x) (x < 0 ? -x : x)
using namespace std;
int solution(int n, int a, int b)
{
    int answer = 1;
    int first = a, second = b;
    while (true) {
        if (ABS((first - second)) <= 1) {
            if (first > second && first % 2 == 0) break;
            if (second > first && second % 2 == 0) break; 
        }
        first = (first % 2) == 0 ? first/2 : (first+1)/2;
        second = second % 2 == 0 ? second/2 : (second+1)/2;
        answer++;
    }
    return answer;
}
```