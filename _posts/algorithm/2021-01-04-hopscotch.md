---
title:  "프로그래머스 Lv.2 - 땅따먹기"
date:   2021-01-04 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12913

## 문제풀이
---

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int solution(vector<vector<int> > land)
{
    int answer = 0;
    int height = land.size(), width = land[0].size();
    vector<vector<int>> dp;
    dp.push_back(land[0]);
    
    for (int i = 1; i < land.size(); i++) {
        vector<int> row;
        for (int j = 0; j < land[0].size(); j++) {
            int max = 0;
            for (int k = 0; k < land[0].size(); k++) {
                if (j == k) continue;
                if (dp[i-1][k] > max) {
                    max = dp[i-1][k];
                }
            }
            row.push_back(max + land[i][j]);
        }
        dp.push_back(row);
    }
    answer = *max_element(dp[height-1].begin(), dp[height-1].end());
    return answer;
}
```