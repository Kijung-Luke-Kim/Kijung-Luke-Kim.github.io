---
title:  "프로그래머스 Lv.1 - 3진법 뒤집기"
date:   2020-11-13 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [monthlycodechallenge, season1]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/68935

자연수 n이 매개변수로 주어집니다. n을 3진법 상에서 앞뒤로 뒤집은 후, 이를 다시 10진법으로 표현한 수를 return 하도록 solution 함수를 완성해주세요.

**제한 사항**   

- n은 1 이상 100,000,000 이하인 자연수입니다.

**입출력 예**

|n|return|
|---|---|
|45|7|
|125|229|


## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <cmath>

using namespace std;

int solution(int n) {
    int answer = 0;
    string sRem = "";
    while (true) {
        if (n < 3) {
            sRem += to_string(n);
            break;
        }
        sRem += to_string(n % 3);
        n /= 3;
    }
    for (int i = 0; i < sRem.size(); i++) {
        answer += (sRem[sRem.size()-1-i]-'0')*pow(3, i);
    }
    return answer;
}
```
