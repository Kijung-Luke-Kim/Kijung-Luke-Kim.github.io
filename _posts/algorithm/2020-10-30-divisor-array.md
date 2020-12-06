---
title:  "프로그래머스 Lv.1 - 나누어 떨어지는 숫자 배열"
date:   2020-11-01 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers, Level1]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12910

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

vector<int> solution(vector<int> arr, int divisor) {
    vector<int> answer;
    sort(arr.begin(), arr.end());
    for (int i = 0; i < arr.size(); i++) {
        if (arr[i] % divisor == 0) {
            answer.push_back(arr[i]);
        }
    }
    if (answer.size()==0) {
        answer.push_back(-1);
    }
    return answer;
}
```