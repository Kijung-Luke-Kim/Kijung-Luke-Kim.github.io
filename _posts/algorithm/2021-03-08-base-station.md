---
title:  "프로그래머스 Lv.3 - 기지국 설치"
date:   2021-03-08 08:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [wintercoding, kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12979

## 문제풀이
---

```cpp
#include <iostream>
#include <vector>
using namespace std;

int solution(int n, vector<int> stations, int w)
{
    int answer = 0, start = 1, index = 0;

    while(start <= n)
    {
        if(start >= stations[index] - w && start <= stations[index] + w)
        {
            start = stations[index] + w;
            index++;
        }
        else
        {
            start += 2 * w;
            answer++;
        }
        start++;
    }

    return answer;
}
```