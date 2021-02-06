---
title:  "프로그래머스 Lv.3 - 섬 연결하기"
date:   2021-02-06 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [greedy]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42861

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

bool comp(vector<int> a, vector<int> b) {
    return a[2] < b[2];
}
int getParent(vector<int> &parent, int x) {
    if (parent[x] == x)
        return x;
    return parent[x] = getParent(parent, parent[x]);
}
void unionParent(vector<int> &parent, int a, int b) {
    a = getParent(parent, a);
    b = getParent(parent, b);
    a < b ? parent[b] = a : parent[a] = b;
}
bool isCycle(vector<int> &parent,  int a, int b) {
    a = getParent(parent, a);
    b = getParent(parent, b);
    return a == b;
}

int solution(int n, vector<vector<int>> costs) {
    int answer = 0;
    vector<int> parent;
    
    for (int i = 0; i < n; i++) {
        parent.push_back(i);
    }
    
    sort(costs.begin(), costs.end(), comp);
    
    for (auto cost : costs) {
        if (!isCycle(parent, cost[0], cost[1])) {
            answer += cost[2];
            unionParent(parent, cost[0], cost[1]);
        }
    }
    
    return answer;
}
```