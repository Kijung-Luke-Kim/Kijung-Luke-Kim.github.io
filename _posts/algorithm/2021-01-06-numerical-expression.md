---
title:  "프로그래머스 Lv.2 - 숫자의 표현"
date:   2021-01-06 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12924

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

int solution(int n) {
    int answer = 0;
    for (int i = 1; i <= n; i++) {
        int sum = i;
        if (i == n) {
            answer++;
            break;
        }
        for (int j = i+1; j <= n; j++) {
            if (sum + j == n) {
                answer++;
                break;
            }
            if (sum + j < n) {
                sum += j;
                continue;
            }
            if (sum + j > n) {
                break;
            }
        }
    }
    return answer;
}
```