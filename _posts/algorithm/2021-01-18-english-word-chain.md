---
title:  "프로그래머스 Lv.2 - 영어 끝말잇기"
date:   2021-01-18 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [wintercoding]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12981

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <set>
#include <iostream>

using namespace std;

vector<int> solution(int n, vector<string> words) {
    vector<int> answer;
    set<string> prev;
    
    for (int i = 0; i < words.size(); i++) {
        auto repeat = prev.insert(words[i]);
        //탈락조건
        if (!repeat.second || words[i].size() < 2 || words[i].size() > 50) {
            answer.push_back(i%n+1);
            answer.push_back(i/n+1);
            break;
        }
        if (i > 0 && words[i-1].back() != words[i].front()) {
            answer.push_back(i%n+1);
            answer.push_back(i/n+1);
            break;
        }
    }
    
    if (answer.size() == 0) {
        answer.push_back(0);
        answer.push_back(0);
    }

    return answer;
}
```