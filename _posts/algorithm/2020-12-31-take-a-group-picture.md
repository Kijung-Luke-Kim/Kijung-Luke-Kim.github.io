---
title:  "프로그래머스 Lv.2 - 단체사진 찍기"
date:   2020-12-31 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/1835

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

int solution(int n, vector<string> data) {
    int answer = 0;
    string members = "ACFJMNRT";
    do {
        answer++;
        for (int i = 0; i < n; ++i) {
            char first = data[i][0];
            char second = data[i][2];
            char cond = data[i][3];
            int dist = data[i][4] - '0';
            int distance = members.find(first) - members.find(second);
            distance = (distance < 0) ? -distance - 1 : distance - 1;
            if (cond == '=' && distance != dist){
                answer--;
                break;
            }
            if (cond == '<' && distance >= dist) {
                answer--;
                break;
            } 
            if (cond == '>' && distance <= dist) {
                answer--;
                break;
            }
        }
    } while (next_permutation(members.begin(), members.end()));
    return answer;
}
```