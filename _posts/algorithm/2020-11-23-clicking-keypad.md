---
title:  "프로그래머스 Lv.1 - [카카오 인턴] 키패드 누르기"
date:   2020-11-23 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/67256

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <cmath>
#include <iostream>

using namespace std;

int Distance(int point1, int point2) {
    int rise = ceil(point1 / 3.0) - ceil(point2 / 3.0);
    int run1 = point1 % 3 == 0 ? 3 : point1 % 3;
    int run2 = point2 % 3 == 0 ? 3 : point2 % 3;
    int run = run1 - run2;
    rise = rise < 0 ? -rise : rise;
    run = run < 0 ? -run : run;
    return rise + run;
}

string solution(vector<int> numbers, string hand) {
    string answer = "";
    int Lat = 10;
    int Rat = 12;
    int LDist;
    int RDist;
    for (int i = 0; i < numbers.size(); i++) {
        int Dat = numbers[i];
        if (Dat == 0) {
            Dat = 11;
        }
        if (Dat == 1) {
            answer += "L";
            Lat= 1;
        }
        else if (Dat == 4) {
            answer += "L";
            Lat= 4;
        }
        else if (Dat == 7) {
            answer += "L";
            Lat= 7;
        }
        else if (Dat == 3) {
            answer += "R";
            Rat= 3;
        }
        else if (Dat == 6) {
            answer += "R";
            Rat= 6;
        }
        else if (Dat == 9) {
            answer += "R";
            Rat= 9;
        }
        else {
            if (Distance(Rat, Dat) == Distance(Lat, Dat)) {
                if (hand == "right"){
                    Rat = Dat;
                    answer += "R";
                }
                else {
                    Lat = Dat;
                    answer += "L";
                }
            }
            else {
                if (Distance(Rat, Dat) > Distance(Lat, Dat)) {
                    Lat = Dat;
                    answer += "L";
                }
                else {
                    Rat = Dat;
                    answer += "R";
                }
            }
        }
    }
    return answer;
}
```
