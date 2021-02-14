---
title:  "프로그래머스 Lv.3 - 입국심사"
date:   2021-02-14 08:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [binarysearch]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/4323828

## 문제풀이
---

```cpp
#include <vector>
#include <algorithm>
 
using namespace std;
 
long long solution(int n, vector<int> times) {
    //정답, 최소시간, 최대시간, 평균시간
    long long answer = 0, minTime = 1, maxTime, avgTime, human = 0;
    //최대값 은 최대인원수 * 인원수
    maxTime = *max_element(times.begin(), times.end()) * (long long)n;
    //최소시간이 최대시간과 같거나 적을때까지 반복
    while (minTime <= maxTime) {
        //평균시간 구하기
        avgTime = ((maxTime + minTime) / 2);
        //현재 시간으로 돌릴수 잇는 최대인원 구하기
        for (auto t : times)        human += avgTime / t;
        //최대인원이 총인원보다 크거나 같다면
        if (n <= human) {
            //현재 시간을 정답에 저장(나중에 안나오면 리턴해야 해서
            answer = avgTime;
            //최대시간 갱신
            maxTime = avgTime - 1;
        }
        //총인원보다 적다면 현재보다 시간이커야하므로 최소시간 갱신
        else    minTime = avgTime + 1;
        //사람수 초기화
        human = 0;
    }
    return answer;
}
```