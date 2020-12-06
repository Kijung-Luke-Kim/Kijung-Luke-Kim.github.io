---
title:  "프로그래머스 Lv.2 - 주식가격"
date:   2020-12-06 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers, Level2]
tags: [stack]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42584

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

vector<int> solution(vector<int> prices) {
    vector<int> answer;
    for (int i = 0; i < prices.size()-1; i++) {
        int period = 0;
        for (int j = i+1; j < prices.size(); j++) {
            if (prices[i] > prices[j]) {
                period++;
                break;
            }
            period++;
        }
        answer.push_back(period);
    }
    answer.push_back(0);
    return answer;
}
```
