---
title:  "프로그래머스 Lv.3 - 하노이의 탑"
date:   2021-03-04 08:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12946

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

int Hanoi(int from, int via, int to, int n, vector<vector<int>> &answer) // from번 기둥에서 to번 기둥으로 n개의 원반을 이동.
{
    vector<int> temp;
    if(n == 1)
    {
        temp.push_back(from);
        temp.push_back(to);
        answer.push_back(temp);
        return 0;
    }

    Hanoi(from, to, via, n-1, answer);
    temp.push_back(from);
    temp.push_back(to);
    answer.push_back(temp);
    Hanoi(via, from, to, n-1, answer);
    return 0;
}

vector<vector<int>> solution(int n) {
    vector<vector<int>> answer;
    Hanoi(1, 2, 3, n, answer);
    return answer;
}
```