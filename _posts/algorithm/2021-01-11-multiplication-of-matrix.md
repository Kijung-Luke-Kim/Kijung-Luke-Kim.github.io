---
title:  "프로그래머스 Lv.2 - 행렬의 곱셈"
date:   2021-01-11 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12949

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

vector<vector<int>> solution(vector<vector<int>> arr1, vector<vector<int>> arr2) {
    vector<vector<int>> answer;
    for (int i = 0; i < arr1.size(); i++) {        
        vector<int> row;
        for (int j = 0; j < arr2[0].size(); j++) {
            int sum = 0;
            for (int k = 0; k < arr2.size(); k++) {
                sum += arr1[i][k] * arr2[k][j];
            }
            row.push_back(sum);
        }
        answer.push_back(row);
    }
    return answer;
}
```