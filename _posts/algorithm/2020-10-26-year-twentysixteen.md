---
title:  "프로그래머스 Lv.1 - 2016년"
date:   2020-10-26 18:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers, Level1]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12901 

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

int monthday(int month) {
    int day = 0;
    switch (month) {
    case 1:
        day = 31;
        break;
    case 2:
        day = 29;
        break;
    case 3:
        day = 31;
        break;
    case 4:
        day = 30;  
        break;
    case 5:
        day = 31;
        break;
    case 6:
        day = 30;
        break;
    case 7:
        day = 31;
        break;
    case 8:
        day = 31;
        break;
    case 9:
        day = 30;
        break;
    case 10:
        day = 31;
        break;
    case 11:
        day = 30;
        break;
    case 12:
        day = 31;
        break;
    }
    return day;
}

string solution(int a, int b) {
    string answer = "";
    int monthdays = 0;
    if (a != 1) {
        for (int i = 1; i < a; i++) {
            monthdays += monthday(i);
        }
    }
    int weekday = (monthdays + b) % 7;
    switch (weekday) {
        case 1:
            answer = "FRI";
            break;
        case 2:
            answer = "SAT";
            break;
        case 3:
            answer = "SUN";
            break;
        case 4:
            answer = "MON";
            break;
        case 5:
            answer = "TUE";
            break;
        case 6:
            answer = "WED";
            break;
        case 0:
            answer = "THU";
            break;
    }
    
    
    return answer;
}
```
