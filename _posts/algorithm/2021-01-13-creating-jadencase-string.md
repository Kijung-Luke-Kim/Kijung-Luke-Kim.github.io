---
title:  "프로그래머스 Lv.2 - JadenCase 문자열 만들기"
date:   2021-01-13 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12951

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

string solution(string s) {
    string answer = "";
    for (int i = 0; i < s.size(); i++) {
        answer.push_back(tolower(s[i]));
    }
    for (int i = 0; i < s.size(); i++) {
        if (i == 0) answer[i] = toupper(s[i]);
        if (s[i] == ' ') {
            answer[i+1] = toupper(s[i+1]);
        }
    } 
    return answer;
}
```