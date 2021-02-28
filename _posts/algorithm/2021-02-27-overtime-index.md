---
title:  "프로그래머스 Lv.3 - 야근 지수"
date:   2021-02-27 08:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice, binarysearch]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12927

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <queue>
#include <numeric>

using namespace std;

long long solution(int n, vector<int> works) {
    long long answer = 0;
    priority_queue<int> pq (works.begin(), works.end());
    if (n >= accumulate(works.begin(), works.end(), 0)) return 0;
    while(n > 0) {
        int cur = pq.top();
        pq.pop();
        pq.push(cur-1);
        --n;
    }
    while (!pq.empty()) {
        answer += pq.top()*pq.top();
        pq.pop();
    }
    return answer;
}
```