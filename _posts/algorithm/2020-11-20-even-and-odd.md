---
title:  "프로그래머스 Lv.1 - 짝수와 홀수"
date:   2020-11-20 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers, Level1]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12937

정수 num이 짝수일 경우 Even을 반환하고 홀수인 경우 Odd를 반환하는 함수, solution을 완성해주세요.

**제한 사항**   

- num은 int 범위의 정수입니다.
- 0은 짝수입니다.

**입출력 예**

|s|return|
|---|---|
|3|"Odd"|
|4|"Even|

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

string solution(int num) {
    string answer = "";
    if (num % 2 == 0) {
        answer = "Even";
    }
    else {
        answer = "Odd";
    }
    return answer;
}
```
