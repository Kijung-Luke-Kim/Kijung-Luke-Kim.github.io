---
title: "프로그래머스 Lv.1 - 완주하지 못한 선수"
author: Kijung Luke Kim
date: 2020-10-19 12:00:00 +0900
categories: [Algorithm, Programmers, Level1]
tags: [hash]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42576

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

string solution(vector<string> participant, vector<string> completion) {
    string answer = "";
    sort(participant.begin(), participant.end());
    sort(completion.begin(), completion.end());
    
    for (int i = 0; i < completion.size(); i++) {
        if (participant[i] != completion[i]) {
            return participant[i];
        }
    }

    return participant[participant.size()-1];
}
```