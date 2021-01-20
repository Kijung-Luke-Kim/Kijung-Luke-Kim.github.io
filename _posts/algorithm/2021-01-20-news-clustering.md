---
title:  "프로그래머스 Lv.2 - [1차] 뉴스 클러스터링"
date:   2021-01-20 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/17677

## 문제풀이
---

```cpp
#include <string>
#include <set>
#include <vector>
#include <algorithm>
#include <iostream>

using namespace std;

int solution(string str1, string str2) {
    int answer = 0;
    multiset<string> set1;
    multiset<string> set2;
    vector<string> intersectionSet(3000);
    vector<string> unionSet(3000);
    for (int i = 0; i < str1.size()-1; i++) {
        if (!isalpha(str1[i]) || !isalpha(str1[i+1])) continue;
        string part = "";
        part.push_back(tolower(str1[i]));
        part.push_back(tolower(str1[i+1]));
        set1.insert(part);
    }
    for (int i = 0; i < str2.size()-1; i++) {
        if (!isalpha(str2[i]) || !isalpha(str2[i+1])) continue;
        string part = "";
        part.push_back(tolower(str2[i]));
        part.push_back(tolower(str2[i+1]));
        set2.insert(part);
    }
    if (set1.empty() && set2.empty()) {
        return 65536;
    }
    auto iter1 = set_intersection(set1.begin(), set1.end(), set2.begin(), set2.end(), intersectionSet.begin());
    auto iter2 = set_union(set1.begin(), set1.end(), set2.begin(), set2.end(), unionSet.begin());
    intersectionSet.resize(iter1-intersectionSet.begin());
    unionSet.resize(iter2-unionSet.begin());
    
    float iS = intersectionSet.size();
    float uS = unionSet.size();
    answer = iS/uS*65536;
    return answer;
}
```