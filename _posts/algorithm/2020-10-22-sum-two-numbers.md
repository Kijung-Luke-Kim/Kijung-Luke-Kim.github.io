---
title: "프로그래머스 Lv.1 - 두 개 뽑아서 더하기"
author: Kijung Luke Kim
date: 2020-10-22 12:00:00 +0900
categories: [Algorithm, Programmers]
tags: [sort]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/68644?language=cpp

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

vector<int> solution(vector<int> numbers) {
    vector<int> answer;
    for (int i = 0; i < numbers.size(); i++) {
        for (int j = 0; j < numbers.size(); j++) {
            if (i == j) continue;
            int sum = numbers[i]+numbers[j];
            if (find(answer.begin(), answer.end(), sum) == answer.end()) {
                answer.push_back(sum);
            }
        }
    }
    sort(answer.begin(), answer.end());
    return answer;
}
```