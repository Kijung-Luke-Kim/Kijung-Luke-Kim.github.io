---
title:  "프로그래머스 Lv.2 - 가장 큰 수"
date:   2020-12-17 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [sort]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42746

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

bool cmp(string a, string b) {
    return a+b > b+a;
}

string solution(vector<int> numbers) {
    string answer = "";
    vector<string> numbers_str;
    vector<string> digit_list;
    for (int i = 0; i < numbers.size(); i++) {
         numbers_str.push_back(to_string(numbers[i]));
    }
    sort(numbers_str.begin(), numbers_str.end(), cmp);
    for (int i = 0 ; i < numbers_str.size(); i++) {
        answer.append(numbers_str[i]);
    }
    if (answer[0] == '0') {
        answer = "0";
    }
    return answer;
}
```