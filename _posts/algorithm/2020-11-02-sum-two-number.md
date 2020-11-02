---
title:  "프로그래머스 Lv.1 - 두 정수 사이의 합"
date:   2020-11-02 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12912

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

long long solution(int a, int b) {
    long long answer = 0;
    if (b > a) {
        for (int i = a; i <= b; i++) {
            answer += i;
        }
    }
    else {
        for (int i = b; i <= a; i++) {
            answer += i;
        }
    }
    return answer;
}
```
