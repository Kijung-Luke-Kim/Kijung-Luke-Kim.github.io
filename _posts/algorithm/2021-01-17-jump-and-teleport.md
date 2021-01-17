---
title:  "프로그래머스 Lv.2 - 점프와 순간 이동"
date:   2021-01-17 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [wintercoding]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12980

## 문제풀이
---

```cpp
#include <iostream>
using namespace std;

int solution(int n)
{
    int ans = 0;   
    while (n > 0) {
        ans += n % 2;
        n /= 2;
    }
    return ans;
}
```