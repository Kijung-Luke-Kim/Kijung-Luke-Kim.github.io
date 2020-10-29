---
title:  "프로그래머스 Lv.1 - 같은 숫자는 싫어"
date:   2020-10-29 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12906

## 문제풀이
---

```cpp
#include <vector>
#include <iostream>

using namespace std;

vector<int> solution(vector<int> arr) 
{
    vector<int> answer;
    
    for (auto it = arr.begin(); it < arr.end(); ++it) {
        if (answer.size() == 0) {
            answer.push_back(*it);
        }
        else if (answer.back() != *it) {
            answer.push_back(*it);
        }
    }

    return answer;
}
```