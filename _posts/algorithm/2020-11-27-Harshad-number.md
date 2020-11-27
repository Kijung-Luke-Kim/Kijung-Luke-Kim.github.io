---
title:  "프로그래머스 Lv.1 - 하샤드 수"
date:   2020-11-27 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12947

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

bool solution(int x) {
    bool answer = true;
    int digitSum = 0;
    string digitStr = to_string(x);
    for (int i = 0; i < digitStr.length(); i++){
        digitSum += (digitStr[i] - '0');
    }
    answer = (x % digitSum == 0);
    return answer;
}
```
