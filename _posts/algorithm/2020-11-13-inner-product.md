---
title:  "프로그래머스 Lv.1 - 내적"
date:   2020-11-13 12:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers, Level1]
tags: [monthlycodechallenge, season1]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/70128

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

int solution(vector<int> a, vector<int> b) {
    int answer = 0;
    for (int i = 0; i < a.size(); i++) {
        answer += a[i]*b[i];
    }
    return answer;
}
```
