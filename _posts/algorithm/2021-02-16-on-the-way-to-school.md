---
title:  "프로그래머스 Lv.3 - 등굣길"
date:   2021-02-16 08:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [dp]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42898

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

int solution(int m, int n, vector<vector<int>> puddles) {
    int answer = 0;
    vector<vector<int>> numPath (n, vector<int> (m, 1));
    vector<vector<bool>> canPass (n, vector<bool>(m, true));
    
    for (auto puddle : puddles) {
        numPath[puddle[1]-1][puddle[0]-1] = 0;
        canPass[puddle[1]-1][puddle[0]-1] = false;
        if (puddle[0] == 1) {
            for (int i = puddle[1]-1; i < n; i++) {
                numPath[i][0] = 0;
            }
        }
        if (puddle[1] == 1) {
            for (int i = puddle[0]-1; i < m; i++) {
                numPath[0][i] = 0;
            }
        }
    }
    for (int i = 1; i < n; i++) {
        for (int j = 1; j < m; j++) {
            if (canPass[i][j]) {
                numPath[i][j] = (numPath[i-1][j] + numPath[i][j-1]) % 1000000007;
            }
        }
    }
    
    answer = numPath[n-1][m-1];
    
    return answer;
}
```