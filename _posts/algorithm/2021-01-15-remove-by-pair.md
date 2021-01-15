---
title:  "프로그래머스 Lv.2 - 짝지어 제거하기"
date:   2021-01-15 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [tipstown]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12973

## 문제풀이
---

```cpp
#include <iostream>
#include <string>
#include <stack>
using namespace std;

int solution(string s)
{
    int answer = 0;
    stack<char> combs;
    for (int i = 0; i < s.size(); i++) {
        if (combs.empty()) combs.push(s[i]);
        else if (s[i] == combs.top()) combs.pop();
        else combs.push(s[i]);
    }
    
    answer = combs.size()==0 ? 1 : 0;
    
    return answer;
}
```