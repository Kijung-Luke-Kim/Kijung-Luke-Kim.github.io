---
title:  "프로그래머스 Lv.2 - 올바른 괄호"
date:   2021-01-02 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12909

## 문제풀이
---

```cpp
#include <string>
#include <iostream>
#include <vector>

using namespace std;

bool solution(string s)
{
    bool answer = true;
    vector<char> stack;
    
    for (int i = 0; i < s.size(); i++) {
        if (s[i]=='(') {
            stack.push_back(s[i]);
        }
        else {
            if (stack.size() > 0)   stack.pop_back();
            else {
                answer = false;
                break;
            }
        }
    }
    if (answer) answer = stack.empty();
    return answer;
}
```