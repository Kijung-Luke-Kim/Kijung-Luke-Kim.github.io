---
title:  "프로그래머스 Lv.3 -가장 긴 팰린드롬"
date:   2021-02-20 08:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice, binarysearch]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12904

## 문제풀이
---

```cpp
#include <iostream>
#include <string>
using namespace std;
int solution(string s)
{
    int answer = s.size();
    while(answer >= 2) {
        for (int i = 0; i <= s.size()-answer; i++) {
            int left = i;
            int right = answer+i-1;
            bool flag = true;
            while (left <= right) {
                if (s[left] != s[right]) {
                    flag = false;
                    break;
                }
                left++;
                right--;
            }
            if (flag)
                return answer;
        }
        answer--;
    }
    return answer;
}
```