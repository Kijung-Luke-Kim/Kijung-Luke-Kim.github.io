---
title:  "프로그래머스 Lv.2 - 최댓값과 최솟값"
date:   2021-01-08 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12939

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

string solution(string s) {
    string answer = "";
    string num = "";
    vector<int> nums;
    for (int i = 0; i < s.size(); i++) {
        if (s[i]==' ') {
            nums.push_back(stoi(num));
            num = "";
        }
        else {
            num.push_back(s[i]);
            if (i == s.size()-1) {
                nums.push_back(stoi(num));
                num = "";
            }
        }
    }
    answer = to_string(*min_element(nums.begin(), nums.end()))+" "+ to_string(*max_element(nums.begin(), nums.end()));
    return answer;
}
```