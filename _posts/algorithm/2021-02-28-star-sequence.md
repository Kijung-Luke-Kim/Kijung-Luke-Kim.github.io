---
title:  "프로그래머스 Lv.3 - 스타 수열"
date:   2021-02-28 08:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/70130

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

int solution(vector<int> a) {
    int answer = -1;
    vector<int> cnt(a.size()+1, 0);
    //횟수 저장
    for (int i = 0; i < a.size(); i++) cnt[a[i]]++;
    
    for (int i = 0; i < cnt.size(); i++) {
        if (cnt[i] <= 1) continue;
        if (cnt[i] <= answer) continue;
        int result = 0;
        for (int j = 0; j < a.size() - 1; j++) {
            if (a[j] != i && a[j+1] != i) continue;
            if (a[j] == a[j+1]) continue;
            result++;
            j++;
        }
        answer = answer > result ? answer : result;
    }
    if (answer < 0) return 0;
    return answer * 2;
}
```