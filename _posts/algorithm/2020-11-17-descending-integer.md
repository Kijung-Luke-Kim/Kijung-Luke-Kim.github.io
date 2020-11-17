---
title:  "프로그래머스 Lv.1 - 정수 내림차순으로 배치하기"
date:   2020-11-17 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12933

함수 solution은 정수 n을 매개변수로 입력받습니다. n의 각 자릿수를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴해주세요. 예를들어 n이 118372면 873211을 리턴하면 됩니다.

**제한 사항**   

- n은 1이상 8000000000 이하인 자연수입니다.

**입출력 예**

|s|return|
|---|---|
|118372|873211|

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

bool desc(int a , int b) {
    return a >= b;
}

long long solution(long long n) {
    long long answer = 0;
    string strn = to_string(n);
    sort(strn.begin(), strn.end(), desc);
    answer = stol(strn);
    return answer;
}
```
