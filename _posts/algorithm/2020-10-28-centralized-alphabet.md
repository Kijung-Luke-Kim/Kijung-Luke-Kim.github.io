---
title:  "Programmers Lv.1 - 가운데 글자 가져오기"
date:   2020-10-28 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12903

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

string solution(string s) {
    string answer = "";
    //홀수
    if (s.length() % 2 == 1) {
        answer = s[int(s.length()/2)];
    }
    else {
        answer += s[int(s.length()/2 - 1)];
        answer += s[int(s.length()/2)];

    }
    return answer;
}
```
