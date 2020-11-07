---
title:  "프로그래머스 Lv.1 - 문자열 다루기 기본"
date:   2020-11-07 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12918

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

bool solution(string s) {
    bool answer = true;
    // if ((s.length() == 4) || (s.length() == 6)) {
    //     for (int i = 0; i < s.length(); i++) {
    //         if (isdigit(s[i]) == false) {
    //             answer = false;
    //             break;
    //         }
    //         else {
    //             answer = true;
    //         }
    //     }
    // }
    // else {
    //     answer = false;
    // }
    if (!((s.length() == 4) || (s.length() == 6))) {
        return false;
    }
    for (int i = 0; i < s.length(); i++) {
        if (isdigit(s[i]) == false) {
            return false;
        }
    }
    return answer;
}
```
