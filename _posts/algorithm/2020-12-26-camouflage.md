---
title:  "프로그래머스 Lv.2 - 위장"
date:   2020-12-26 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [hash]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42578

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <map>

using namespace std;

int solution(vector<vector<string>> clothes) {
    int answer = 1;
    map<string, int> spy;
    for (int i = 0; i < clothes.size(); i++) {
        spy.insert(make_pair(clothes[i][1], 0));
    }
    for (auto iter = spy.begin(); iter != spy.end(); ++iter) {
        for (int i = 0; i < clothes.size(); i++) {
            if (iter->first == clothes[i][1]) {
                iter->second++;
            }
        }
    }
    for (auto iter = spy.begin(); iter != spy.end(); ++iter) {
        answer *= iter->second + 1;
    }
    return --answer;
}
```