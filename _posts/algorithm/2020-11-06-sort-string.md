---
title:  "프로그래머스 Lv.1 - 문자열 내림차순으로 배치하기"
date:   2020-11-06 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12917

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

bool desc (int a, int b) {
    return a > b;
}

string solution(string s) {
    string answer = "";
    sort(s.begin(), s.end(), desc);
    answer = s;
    return answer;
}
```
