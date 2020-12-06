---
title:  "프로그래머스 Lv.1 - 콜라츠 추측"
date:   2020-11-25 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers, Level1]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12943

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

int solution(int num) {
    int answer = 0;
    long given = num;
    while (given != 1) {
        if (answer == 500) {
            answer = -1;
            break;
        }
        if (given % 2 == 0) {
            given = given / 2;
        }
        else {
            given = given*3 + 1;
        }
        ++answer;
    }
    return answer;
}
```
