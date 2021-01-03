---
title:  "프로그래머스 Lv.2 - 다음 큰 숫자"
date:   2021-01-03 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12911

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <bitset>

using namespace std;

int solution(int n) {
    int answer = 0;
    bitset<32> binary(n);
    string sBinary = binary.to_string();
    int sCount = 0;
    for (int i = 0 ; i < 32; i++) {
        if (sBinary[i] == '1') sCount++;
    }
    while(true) {
        n++;
        bitset<32> compare(n);
        string sCompare = compare.to_string();
        int cCount = 0;
        for (int i = 0 ; i < 32; i++) {
            if (sCompare[i] == '1') cCount++;
        }
        if (cCount == sCount) {
            answer = n;
            break;
        }
    }
    return answer;
}
```