---
title:  "프로그래머스 Lv.2 - 타겟 넘버"
date:   2020-12-27 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [DFS]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/43165

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;
int answer = 0;
void DFS(vector<int> nums, int tar, int pos, int sum) {
    if (pos == nums.size()) {
        if (sum == tar) {
            answer++;
            return;
        }
    }
    else {
        DFS(nums, tar, pos+1, sum+nums[pos]);
        DFS(nums, tar, pos+1, sum-nums[pos]);
    }
}
int solution(vector<int> numbers, int target) {
    DFS(numbers, target, 0, 0);
    return answer;
}
```