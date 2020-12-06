---
title:  "프로그래머스 Lv.1 - 문자열 내 p와 y의 개수"
date:   2020-11-05 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers, Level1]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12916

## 문제풀이
---

```cpp
#include <string>
#include <iostream>
using namespace std;

bool solution(string s)
{
    bool answer = true;

    int pCount = 0;
    int yCount = 0;
    
    for (int i = 0; i < s.length(); i++) {
        if ((s[i] == 'p') || (s[i] == 'P')) {
            ++pCount;
        }
        if ((s[i] == 'y') || (s[i] == 'Y')) {
            ++yCount;
        }
    }
    
    answer = (pCount == yCount);
    
    return answer;
}
```
