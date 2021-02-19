---
title:  "프로그래머스 Lv.3 - 보행자 천국"
date:   2021-02-19 08:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [dp, kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/1832

## 문제풀이
---

```cpp
#include <vector>

using namespace std;

int MOD = 20170805;

// 전역 변수를 정의할 경우 함수 내에 초기화 코드를 꼭 작성해주세요.
int solution(int m, int n, vector<vector<int>> city_map) {
    int answer = 0;
    vector<vector<int>> numPathFromTop(m+1, vector<int>(n+1, 0));
    vector<vector<int>> numPathFromLeft(m+1, vector<int>(n+1, 0));
    
    numPathFromTop[1][1] = numPathFromLeft[1][1] = 1;
    
    for (int i = 1; i <= m; i++) {
        for (int j = 1; j <= n; j++) {
            if (city_map[i-1][j-1] == 0) {
                numPathFromTop[i][j] += (numPathFromTop[i][j-1] + numPathFromLeft[i-1][j])% MOD;
                numPathFromLeft[i][j] += (numPathFromTop[i][j-1] + numPathFromLeft[i-1][j])% MOD;
            }
            if (city_map[i-1][j-1] == 1) {
                numPathFromTop[i][j] = 0;
                numPathFromLeft[i][j] = 0;
            }
            if (city_map[i-1][j-1] == 2) {
                numPathFromTop[i][j] += numPathFromTop[i][j-1];
                numPathFromLeft[i][j] += numPathFromLeft[i-1][j];
            }
        }
    }
    answer = numPathFromTop[m][n] % MOD;
    return answer;
}
```