---
title:  "프로그래머스 Lv.1 - 문자열 내 마음대로 정렬하기"
date:   2020-11-04 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers, Level1]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12915

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>

using namespace std;
bool myfunc(string i, string j) {
    
}
vector<string> solution(vector<string> strings, int n) {
    vector<string> answer;
    for (auto iterStr = strings.begin(); iterStr < strings.end(); ++iterStr) {
        string word = *iterStr;
        word = word[n] + word;
        *iterStr = word;
    }
    sort(strings.begin(), strings.end());
    for (auto iterStr = strings.begin(); iterStr < strings.end(); ++iterStr) {
        string word = *iterStr;
        *iterStr = word.substr(1);
    }
    answer = strings;
    return answer;
}
```
