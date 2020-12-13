---
title:  "프로그래머스 Lv.2 - 기능개발"
date:   2020-12-13 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [stack, queue]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42586

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>
using namespace std;

vector<int> solution(vector<int> progresses, vector<int> speeds) {
    vector<int> answer;
    vector<int> days;
    vector<int> works;
    for (int i = 0; i < progresses.size(); i++) {
        days.push_back((100 - progresses[i])/speeds[i] + ((100 - progresses[i])%speeds[i] != 0));
    }
    for (int i = 0; i < days.size(); i++) {
        if (works.size() == 0) {
            works.push_back(days[i]);
        }
        else {
            sort(works.begin(), works.end());
            if (works.back() < days[i]) {
                answer.push_back(works.size());
                works.clear();
                works.push_back(days[i]);
            }
            else {
                works.push_back(days[i]);
            }
        }
    }
    answer.push_back(works.size());
    return answer;
}
```