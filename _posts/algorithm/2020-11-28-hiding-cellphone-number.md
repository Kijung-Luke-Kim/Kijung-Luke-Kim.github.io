---
title:  "프로그래머스 Lv.1 - 핸드폰 번호 가리기"
date:   2020-11-28 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers, Level1]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12948

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

string solution(string phone_number) {
    string answer = phone_number;
    for (int i = 0; i < answer.length()-4;i++) {
        answer[i] = '*';
    }
    return answer;
}
```
