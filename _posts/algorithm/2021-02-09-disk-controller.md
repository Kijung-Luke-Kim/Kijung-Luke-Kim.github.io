---
title:  "프로그래머스 Lv.3 - 디스크 컨트롤러"
date:   2021-02-09 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [heap]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42627

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <queue>

using namespace std;

struct cmp {
    bool operator()(vector<int> a, vector<int> b) {
        return (a.at(1) > b.at(1));
    }
};

int solution(vector<vector<int>> jobs) {
    int answer = 0, i = 0, time = 0;
    sort(jobs.begin(), jobs.end());
    priority_queue<vector<int>, vector<vector<int>>, cmp> pq;  
    
    while (i < jobs.size() || !pq.empty()) {
        if (i < jobs.size() && time >= jobs[i][0]) {
            pq.push(jobs[i++]);
            continue;
        }
        if (!pq.empty()) {
            time += pq.top()[1];
            answer += time - pq.top()[0];
            pq.pop();
        }
        else {
            time = jobs[i][0];
        }
    }    
    
    return answer/jobs.size();
}
```