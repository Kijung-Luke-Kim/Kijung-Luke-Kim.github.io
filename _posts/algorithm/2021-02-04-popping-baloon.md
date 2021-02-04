---
title:  "프로그래머스 Lv.3 - 풍선 터트리기"
date:   2021-02-04 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [monthlycodingchallenge]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/68646

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>

using namespace std;

int solution(vector<int> a) {
    int answer = 2;
    vector<int> dpLeft (a.size(), 0);
    vector<int> dpRight (a.size(), 0);
    dpLeft[0] = a[0];
    dpRight[a.size()-1] = a[a.size()-1];
    for (int i = 1; i < a.size(); i++) {
        if (a[i] < dpLeft[i-1]) dpLeft[i] = a[i];
        else dpLeft[i] = dpLeft[i-1];
        if (a[a.size()-i-1] < dpRight[a.size()-i]) dpRight[a.size()-i-1] = a[a.size()-i-1];
        else dpRight[a.size()-i-1] = dpRight[a.size()-i];
    }
    for (int i = 1; i < a.size()-1; i++) {
        int count = 0;
        int minleft = dpLeft[i-1];
        int minright = dpRight[i+1];
        if (a[i] > minleft)
            count++;
        if (a[i] > minright)
            count++;
        if (count <= 1) {
            //cout << a[i] << endl;
            answer++;
        }
    }
    
    
    return answer;
}
```