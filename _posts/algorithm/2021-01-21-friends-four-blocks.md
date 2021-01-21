---
title:  "프로그래머스 Lv.2 - [1차] 프렌즈4블록"
date:   2021-01-21 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/17679

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

int solution(int m, int n, vector<string> board) {
    int answer = 0;
    bool erase = true;
    while (erase) {
        bool erased[30][30] = { false, };
        erase = false;
        //터뜨릴꺼 판별
        for (int i = 0; i < m-1; i++) {
            for (int j = 0; j < n-1; j++) {
                if (board[i][j] == '0') continue;
                if (board[i][j] == board[i][j+1] &&
                    board[i][j] == board[i+1][j] &&
                    board[i][j] == board[i+1][j+1]) {
                    erased[i][j] = true;
                    erased[i][j+1] = true;
                    erased[i+1][j] = true;
                    erased[i+1][j+1] = true;
                    erase = true;
                }
            }
        }
        if (!erase) break;
        //터뜨리기
        for (int i = 0; i < m; i++) {
            for (int j = 0; j < n; j++) {
                if (erased[i][j]) board[i][j] = '0';
            }
        }
        //터진 자리 채우기
        for (int i = 0 ; i < n; i++) {
            for (int j = m-1; j >=0; j--) {
                if (board[j][i] != '0') continue;
                for (int k = j-1; k >= 0; k--) {
                    if (board[k][i] == '0') continue;
                    auto temp = board[k][i];
                    board[j][i] = board[k][i];
                    board[k][i] = '0';
                    break;
                }
            }
        }
    }
    for (int i = 0; i < m; i++) {
        for (int j = 0; j < n; j++) {
            if (board[i][j] == '0') answer++;
        }
    }
    return answer;
}
```