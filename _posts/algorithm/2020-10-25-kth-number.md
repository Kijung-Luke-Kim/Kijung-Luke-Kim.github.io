---
title:  "프로그래머스 Lv.1 - K번째수"
date:   2020-10-25 12:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers, Level1]
tags: [sort]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42748

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

vector<int> solution(vector<int> array, vector<vector<int>> commands) {
    vector<int> answer;
    for (auto it = commands.begin(); it != commands.end(); ++it) {
        vector<int> command = *it;
        int i = command[0];
        int j = command[1];
        int k = command[2];
        vector<int> result;
        for (int l = i-1; l < j; l++) {
            result.push_back(array[l]);
        }
        sort(result.begin(), result.end());
        answer.push_back(result[k-1]);         
    }
    return answer;
}
```
