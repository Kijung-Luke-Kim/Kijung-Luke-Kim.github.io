---
title:  "프로그래머스 Lv.1 - [1차] 비밀지도"
date:   2020-12-03 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers, Level1]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/17681

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <bitset>
#include <algorithm>

using namespace std;

vector<string> solution(int n, vector<int> arr1, vector<int> arr2) {
    vector<string> answer;
    string ans;
    for (int i = 0; i < n; ++i) {
        ans = bitset<16>(arr1[i]|arr2[i]).to_string();
        for (int j = 0; j < ans.length(); j++) {
            ans[j]=='1' ? ans[j]='#' : ans[j]=' ';
        }
        reverse(ans.begin(), ans.end());
        ans = ans.substr(0,n);
        reverse(ans.begin(), ans.end());
        answer.push_back(ans);
    }
    return answer;
}
```
