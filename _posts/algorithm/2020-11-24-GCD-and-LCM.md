---
title:  "프로그래머스 Lv.1 - 최대공약수와 최소공배수"
date:   2020-11-24 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12940

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

int GCF(int a, int b) {
    int ans;
    for (int i = 1; i <= min(a, b); i++) {
        if ((a % i == 0) && (b % i == 0)) {
            ans = i;
        }
    }
    return ans;
}

int LCM(int a, int b) {
    int ans;
    for (int i = min(a, b); i <= a*b; i++) {
        if ((i%a == 0) && (i%b == 0)) {
            ans = i;
            break;
        }
    }
    return ans;
}

vector<int> solution(int n, int m) {
    vector<int> answer;
    answer.push_back(GCF(n, m));
    answer.push_back(LCM(n, m));   
    return answer;
}
```
