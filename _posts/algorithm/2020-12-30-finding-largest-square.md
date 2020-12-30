---
title:  "프로그래머스 Lv.2 - 가장 큰 정사각형 찾기"
date:   2020-12-30 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12905

## 문제풀이
---

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int solution(vector<vector<int>> board)
{
    int answer = 0;
    if (board.size() == 1) answer = 1;

    vector<vector<int>> sideTable;
    
    for (int i = 0; i < board.size(); i++) {
        vector<int> side;
        for (int j = 0; j < board[0].size(); j++) {
            side.push_back(board[i][j]);
        }
        sideTable.push_back(side);
    }
    for (int i = 0; i < board.size(); i++) {
        if (i == 0) continue;
        for (int j = 0; j < board[0].size(); j++) {
            if (j == 0) continue;
            if (board[i][j] == 1) sideTable[i][j] = min(min(sideTable[i-1][j-1], sideTable[i][j-1]), sideTable[i-1][j])+1;
            if (sideTable[i][j] * sideTable[i][j] > answer) answer = sideTable[i][j]*sideTable[i][j];
        }
    }
    return answer;
}
```