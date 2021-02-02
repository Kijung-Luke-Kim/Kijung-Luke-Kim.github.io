---
title:  "프로그래머스 Lv.3 - N으로 표현"
date:   2021-02-01 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [dp]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12900

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

int solution(int n) {
    int answer = 0;
    vector<int> answers;
    answers.push_back(0);
    answers.push_back(1);
    answers.push_back(2);
    for (int i = 3; i <= n; i++) {
        answers.push_back((answers[i-1]+answers[i-2])%1000000007);
    }
    answer = answers[n];
    return answer;
}
```