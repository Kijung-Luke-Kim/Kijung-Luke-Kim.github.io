---
title:  "프로그래머스 Lv.1 - 시저 암호"
date:   2020-11-13 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12928

정수 n을 입력받아 n의 약수를 모두 더한 값을 리턴하는 함수, solution을 완성해주세요.
**제한 사항**   

- n은 0 이상 3000이하인 정수입니다.

**입출력 예**

|n|return|
|---|---|
|12|28|
|5|6|

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

int solution(int n) {
    int answer = 0;
    for (int i = 1; i <= n; i++) {
        if (n % i == 0) {
            answer += i;
        }
    }
    return answer;
}
```
