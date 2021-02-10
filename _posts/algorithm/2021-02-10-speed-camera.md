---
title:  "프로그래머스 Lv.3 - 단속카메라"
date:   2021-02-10 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [greedy]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42884

## 문제풀이
---

```cpp
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

bool compare(vector<int> a, vector<int> b) {
    return a[1] < b[1];
}

int solution(vector<vector<int>> routes) {
    int answer = 0;
    vector<int> cameras;
    sort(routes.begin(), routes.end(), compare);
    for (int i = 0; i < routes.size(); i++) {
        //카메라 범위 확인
        bool metCamera = false;
        for (int j = 0; j < cameras.size(); j++) {
            if (cameras[j] >= routes[i][0] && cameras[j] <= routes[i][1]) {
                metCamera = true;
                break;
            }
        }
        if (!metCamera) {
            cameras.push_back(routes[i][1]);
        }
    }
    answer = cameras.size();
    for (auto cam : cameras) {
        cout << cam << endl;
    }
    return answer;
}
```