---
title:  "프로그래머스 Lv.2 - 폰켓몬"
date:   2021-01-05 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [findprogrammingmaester]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/1845

## 문제풀이
---

```cpp
#include <vector>
#include <set>
using namespace std;

int solution(vector<int> nums)
{
    set<int> variety;
    int answer = 0;
    int nKind = 0;
    int nReq = nums.size() / 2;
    for (int i = 0; i < nums.size(); ++i) {
        variety.insert(nums[i]);
    }
    nKind = variety.size();
    answer = (nKind <= nReq) ? nKind : nReq;
    return answer;
}
```