---
title:  "프로그래머스 Lv.2 - 124 나라의 숫자"
date:   2020-12-09 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12899

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

string solution(int n) {
    string answer = "";
    int share = n;
    while(share!=0) {
        int remainder = share % 3;
        share = share / 3;
        if (remainder == 0) {
            answer = "4" + answer;
            share--;
        }
        else if (remainder == 1){
            answer = "1" + answer;
        }
        else if (remainder == 2){
            answer = "2" + answer;
        }      
    }
    return answer;
}
```
