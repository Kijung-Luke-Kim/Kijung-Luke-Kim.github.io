---
title:  "프로그래머스 Lv.1 - 정수 제곱근 판별"
date:   2020-11-18 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12934

임의의 양의 정수 n에 대해, n이 어떤 양의 정수 x의 제곱인지 아닌지 판단하려 합니다.
n이 양의 정수 x의 제곱이라면 x+1의 제곱을 리턴하고, n이 양의 정수 x의 제곱이 아니라면 -1을 리턴하는 함수를 완성하세요.

**제한 사항**   

- n은 1이상, 50000000000000 이하인 양의 정수입니다.

**입출력 예**

|s|return|
|---|---|
|121|144|
|3|-1|

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <cmath>

using namespace std;

long long solution(long long n) {
    long long answer = 0;
    if (long(sqrt(n))*long(sqrt(n)) == n) {
        return (sqrt(n)+1)*(sqrt(n)+1);
    }
    else {
        return -1;
    }
    return answer;
}
```
