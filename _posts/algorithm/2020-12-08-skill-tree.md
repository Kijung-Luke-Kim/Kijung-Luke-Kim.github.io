---
title:  "프로그래머스 Lv.2 - 스킬 트리"
date:   2020-12-08 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [wintercoding]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/49993

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <iostream>

using namespace std;

int solution(string skill, vector<string> skill_trees) {
    int answer = 0;
    bool skilcap = false;
    for (auto it = skill_trees.begin(); it < skill_trees.end(); ++it) {
        string temp = *it;
        string temp1 = "";
        for (int i = 0; i < temp.size(); i++) {
            for (int j = 0; j < skill.size(); j++) {
                if (temp[i] == skill[j]) {
                    temp1.push_back(temp[i]);
                }
            }
        }
        if (temp1.size() == 0) {
            answer++;
            continue;
        }
        for (int i = 0; i < temp1.size(); i++) {
            if (temp1[i] != skill[i]) {
                skilcap = false;
                break;
            }
            else {
                skilcap = true;
            }
        }
        if (skilcap == true) {
            cout << temp << " "<< temp1 << endl;
            answer++;
        }
    }
    return answer;
}
```
