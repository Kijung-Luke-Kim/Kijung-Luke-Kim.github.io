---
title:  "프로그래머스 Lv.1 - x만큼 간격이 있는 n개의 숫자"
date:   2020-11-30 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12954

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <cmath>

using namespace std;

vector<long long> solution(int x, int n) {
    vector<long long> answer;
    for (int i = 0; i <n; i++) {
        answer.push_back(x+x*(i));
    }
    return answer;
}
```
