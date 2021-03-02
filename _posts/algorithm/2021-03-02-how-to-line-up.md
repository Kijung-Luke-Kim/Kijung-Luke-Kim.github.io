---
title:  "프로그래머스 Lv.3 - 줄 서는 방법"
date:   2021-03-02 08:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12936

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <cmath>

using namespace std;

vector<int> solution(int n, long long k) {
    vector<int> answer;
    // 순열함수를 이용한 방법 (효율성 테스트에서 시간초과 뜸!)
    // vector<int> first;
    // int count = 1;
    // for (int i = 1; i <= n; i++) {
    //     first.push_back(i);
    // }
    // while (count < k) {
    //     next_permutation(first.begin(), first.end());
    //     count++;
    // }
    // return first;
    
    vector<long long> factorial;
    vector<int> waiting;
    
    factorial.push_back(1);
    for (int i = 1; i < n; i++) {
        factorial.push_back(i*factorial[i-1]);
    }
    for (int i = 1; i <= n; i++) {
        waiting.push_back(i);
    }
    
    for (int pos = 0; pos < n; pos++) {
        int ind = ceil(k/(double)factorial[n-1-pos]) - 1;
        answer.push_back(waiting[ind]);
        waiting.erase(waiting.begin()+ind);
        k = k % factorial[n-1-pos];
        if (k == 0)
            k = factorial[n-1-pos];
    }
    
    return answer;
}
```