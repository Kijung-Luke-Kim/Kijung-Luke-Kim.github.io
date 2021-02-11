---
title:  "프로그래머스 Lv.3 - 정수 삼각형"
date:   2021-02-12 08:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [dp]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/43105

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

int solution(vector<vector<int>> triangle) {
    int answer = 0;
    vector<vector<int>> max_sum (triangle.size(), vector<int>(triangle.size()));
    max_sum[0][0] = triangle[0][0];
    for (int i = 1; i < triangle.size(); i++) {
        for (int j = 0; j <= i; j++) {
            if (j == 0) {
                max_sum[i][j] = max_sum[i-1][j] + triangle[i][j];
            }
            else if (j < i) {
                max_sum[i][j] = max_sum[i-1][j-1] + triangle[i][j] > max_sum[i-1][j] + triangle[i][j] ? 
                                max_sum[i-1][j-1] + triangle[i][j] : 
                                max_sum[i-1][j] + triangle[i][j];
            }
            else {
                max_sum[i][j] = max_sum[i-1][j-1] + triangle[i][j];
            }
        }
    }
    answer = *max_element(max_sum[max_sum.size()-1].begin(), max_sum[max_sum.size()-1].end());
    return answer;
}
```