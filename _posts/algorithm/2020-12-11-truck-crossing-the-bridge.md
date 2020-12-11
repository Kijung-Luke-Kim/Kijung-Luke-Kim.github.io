---
title:  "프로그래머스 Lv.2 - 다리를 지나는 트럭"
date:   2020-12-10 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [stack, queue]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42583

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <queue>

using namespace std;

int solution(int bridge_length, int weight, vector<int> truck_weights) {
    int answer = 0;
    vector<pair<int, int>> crossing;
    queue<int> waiting;
    queue<int> finished;
    int bridge_weights = 0;
    
    
    for (int i = 0; i < truck_weights.size(); i++) {
        waiting.push(truck_weights[i]);
    }
    
    while(finished.size() != truck_weights.size()) {
        if (waiting.size() > 0) {
            if (bridge_weights + waiting.front() <= weight) {
                bridge_weights += waiting.front();
                crossing.push_back(make_pair(waiting.front(), 0));
                waiting.pop();
            }
        }
        if (crossing.size() > 0) {
            for (int i = 0; i < crossing.size(); i++) {
                int temp = crossing[i].second;
                crossing[i].second = temp+1;
            }
            if (crossing[0].second == bridge_length) {
                bridge_weights -= crossing.begin()->first;
                finished.push(crossing.begin()->first);
                crossing.erase(crossing.begin());
            }
        }              
        answer++;
    }
    return answer+1;
}
```