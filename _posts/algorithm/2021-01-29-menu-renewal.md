---
title:  "프로그래머스 Lv.2 - 메뉴 리뉴얼"
date:   2021-01-29 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/72411

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <iostream>

using namespace std;

string dtos(int a) {
    string result = "";
    switch (a-9) {
        case 1:
            result.push_back('A');
            break;
        case 2:
            result.push_back('B');
            break;
        case 3:
            result.push_back('C');
            break;
        case 4:
            result.push_back('D');
            break;
        case 5:
            result.push_back('E');
            break;
        case 6:
            result.push_back('F');
            break;
        default:
            result.append(to_string(a));
            break;
    }
    return result;
}

string solution(int n, int t, int m, int p) {
    string answer = "";
    string response = "";
    for (int i = 0; i < t*m; i++) {
        int div = i / n;
        int res = i % n;
        string sRes = dtos(res);
        while (true) {
            if (div == 0) break;
            else {
                res = div % n;
                div = div / n;   
                sRes += dtos(res);
            }
        }
        while (sRes.size() > 0) {
            response.push_back(sRes.back());
            sRes.pop_back();
        }
    }
    for (int i = p-1; i < t*m; i = i+m) {
        answer.push_back(response[i]);
    }
    return answer;
}
```