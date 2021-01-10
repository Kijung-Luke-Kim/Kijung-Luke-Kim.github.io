---
title:  "프로그래머스 Lv.2 - 피보나치 수"
date:   2021-01-10 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12945

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

int solution(int n) {
    int answer = 0;
    vector<long> fib;
    fib.push_back(0);
    fib.push_back(1);
    for (long i = 2; i <= n; i++) {
        fib.push_back((fib[i-1] + fib[i-2])% 1234567l);
    }
    answer = fib[n];
    return answer;
}
```