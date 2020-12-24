---
title:  "프로그래머스 Lv.2 - 전화번호 목록"
date:   2020-12-24 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [hash]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42577

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>

using namespace std;

bool solution(vector<string> phone_book) {
    bool answer = true;
    sort(phone_book.begin(), phone_book.end());
    for (int i = 0; i < phone_book.size()-1; i++) {
        for (int j = i+1; j < phone_book.size(); j++) {
            if (phone_book[i] == phone_book[j].substr(0, phone_book[i].size())) {
                return false;
            }
        }
    }
    return answer;
}
```