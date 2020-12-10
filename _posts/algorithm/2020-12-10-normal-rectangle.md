---
title:  "프로그래머스 Lv.2 - 멀쩡한 사각형"
date:   2020-12-10 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [wintercoding]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/62048

## 문제풀이
---

```cpp
#include <iostream>
#include <algorithm> 
using namespace std;

long long solution(int w,int h) {
    long long answer = 1;
    long long gcd = __gcd(w, h);
    if (gcd == 1) {
        answer = long(w)*h - (w + h - 1);
    }
    else {
        answer = long(w)*h - (w+h-__gcd(w, h));
    }
    
    return answer;
}
```