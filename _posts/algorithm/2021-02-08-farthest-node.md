---
title:  "프로그래머스 Lv.3 - 가장 먼 노드"
date:   2021-02-08 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [graph]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/49189

## 문제풀이
---

```cpp
#include <iostream>
#include <string>
#include <vector>
#include <queue>
#include <algorithm>

using namespace std;

int solution(int n, vector<vector<int>> edge) {
    int answer = 0;
    queue<int> n_queue;
    vector<int> distances(n, 0);
    vector<bool> visited (n, false);
    vector<vector<vector<int>>> edges(n);
    
    for (auto e : edge) {
        edges[e[0]-1].push_back(e);
        edges[e[1]-1].push_back(e);
    }
    
    visited[0] = true;
    n_queue.push(1);
    while(!n_queue.empty()) {
        int temp = n_queue.front();
        n_queue.pop();
        for (auto e : edges[temp-1]) {
            if (e[0] == temp && !visited[e[1]-1]) {
                visited[e[1]-1] = true;
                n_queue.push(e[1]);
                distances[e[1]-1] = distances[temp-1]+1;
            }
            else if (e[1] == temp && !visited[e[0]-1]) {
                visited[e[0]-1] = true;
                n_queue.push(e[0]);
                distances[e[0]-1] = distances[temp-1]+1;
            }
        }
    }
    
    int maxd = *max_element(distances.begin(), distances.end());
    answer = count(distances.begin(), distances.end(), maxd);
    
    return answer;
}
```