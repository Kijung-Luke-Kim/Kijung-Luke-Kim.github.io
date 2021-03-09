---
title:  "프로그래머스 Lv.3 - 숫자 게임"
date:   2021-03-09 08:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [wintercoding, kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12987

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

int solution(vector<int> A, vector<int> B) {
    int answer = 0;
    int idxA = 0, idxB = 0;
    sort(A.begin(), A.end(), greater<int>());
    sort(B.begin(), B.end(), greater<int>());
    while(idxA < A.size()) {
        if (B[idxB] > A[idxA]) {
            idxB++;
            answer++;
        }
        idxA++;
    }
    return answer;
}
```