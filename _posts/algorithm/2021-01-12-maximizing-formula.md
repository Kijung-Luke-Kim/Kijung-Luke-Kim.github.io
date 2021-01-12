---
title:  "프로그래머스 Lv.2 - 수식 최대화"
date:   2021-01-12 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/67257

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>

#define ABS(x) ((x < 0) ? -x : x) 

using namespace std;

long long solution(string expression) {
    long long answer = 0;
    string operators = "*+-";
    vector<long long> results;
    while (true) {
        string num = "";
        vector<string> values;
        for (int i = 0; i < expression.size(); i++) {
            if (expression[i] == '+' || expression[i] == '-' || expression[i] == '*') {
                values.push_back(num);
                num = "";
                num.push_back(expression[i]);
                values.push_back(num);
                num = "";
            }
            else {
                num.push_back(expression[i]);
                if (i == expression.size()-1) {
                    values.push_back(num);
                    num = "";
                }
            }
        }
        for (char c : operators) {
            string sC = string(1, c);
            while (true) {
                auto iter = find(values.begin(), values.end(), sC);
                if (iter == values.end()) break;
                long long value;
                switch (c) {
                    case '+' :
                        value = stol(*(iter-1))+stol(*(iter+1));
                        *iter = to_string(value);
                        values.erase(iter+1);
                        values.erase(iter-1);
                        break;
                    case '-' :
                        value = stol(*(iter-1))-stol(*(iter+1));
                        *iter = to_string(value);
                        values.erase(iter+1);
                        values.erase(iter-1);
                        break;
                    case '*' :
                        value = stol(*(iter-1))*stol(*(iter+1));
                        *iter = to_string(value);
                        values.erase(iter+1);
                        values.erase(iter-1);
                        break;
                }
            }
        }
        results.push_back(ABS(stol(values[0])));
        if (!next_permutation(operators.begin(), operators.end())) {
            break;
        }
    }
    answer = *max_element(results.begin(), results.end());
    return answer;
}
```