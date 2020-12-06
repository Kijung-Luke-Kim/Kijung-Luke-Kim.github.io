---
title:  "프로그래머스 Lv.1 - 행렬의 덧셈"
date:   2020-11-29 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers, Level1]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12950

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

vector<vector<int>> solution(vector<vector<int>> arr1, vector<vector<int>> arr2) {
    vector<vector<int>> answer = arr1;
    for (int i = 0; i < answer.size(); i++) {
        for (int j = 0; j < answer[0].size(); j++) {
            answer[i][j] += arr2[i][j];
        }
    }
    return answer;
}
```
