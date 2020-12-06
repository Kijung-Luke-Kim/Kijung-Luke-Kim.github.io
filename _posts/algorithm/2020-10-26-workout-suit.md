---
title:  "프로그래머스 Lv.1 - 체육복"
date:   2020-10-26 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers, Level1]
tags: [greedy]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42862

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

int solution(int n, vector<int> lost, vector<int> reserve) {
    vector<int> list(n, 1);
    int answer=0;
    //체육복 도난
    for (int i = 0; i < lost.size(); i++) {
        list[lost[i] - 1]--;
    }
    //여벌 체육복
    for (int i = 0; i < reserve.size(); i++) {
        list[reserve[i] - 1]++;
    }
    for (int i = 0; i < list.size(); i++) {
        //현재 보유 체육복 0일시
        if (list[i] == 0) {
            //첫번째 학생이 아니고 이전 학생이 여분 보유시 대여
            if (i != 0 && list[i - 1] == 2) {
                list[i - 1]--;
                list[i]++;
            }
            //마지막 학생이 아니고 다음 학생이 여분 보유시 대여
            else if (i != list.size() - 1 && list[i + 1] == 2) {
                list[i + 1]--;
                list[i]++;
            }
        }
    }
    for (int i = 0; i < list.size(); i++) {
        if (list[i] !=0) {
            answer++;
        }
    }
    return answer;
}
```
