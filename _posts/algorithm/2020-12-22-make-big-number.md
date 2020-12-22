---
title:  "프로그래머스 Lv.2 - 큰 수 만들기"
date:   2020-12-22 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [greedy]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42883

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <queue>

using namespace std;

string solution(string number, int k) {
    string answer = "";
    queue<int> ind;
    for (int i = 0; i < number.size(); i++) {
        if (k == 0) {
            break;
        }
        for (int j = i+1; j < i+k+1; j++) {
            if (number[j] > number[i]) {
                ind.push(i);
                k--;
                break;
            }
        }
    }
    while (k > 0) {
        ind.push(number.size()-k);
        k--;
    }
    int delInd = ind.front(); 
    for (int i = 0; i < number.size(); i++) {
        if (i == delInd) {
            ind.pop();
            delInd = ind.front(); 
        }
        else answer.push_back(number[i]);
    }
    return answer;
}
```