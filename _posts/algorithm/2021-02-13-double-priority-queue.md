---
title:  "프로그래머스 Lv.3 - 이중우선순위큐"
date:   2021-02-13 08:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [heap]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42628

## 문제풀이
---

```cpp
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

vector<int> solution(vector<string> operations) {
    vector<int> answer;
    vector<int> pq;
    
    for (int i = 0; i < operations.size(); i++) {
        //삽입 연산
        if (operations[i][0] == 'I') {
            int data = stoi(operations[i].substr(2));
            cout << "Insert: " << data << endl;
            pq.push_back(data);
            sort(pq.begin(), pq.end());
        }
        //삭제 연산
        else if (operations[i][0] == 'D' && !pq.empty()) {
            //최댓값 삭제
            if (operations[i][2] == '1') {
                cout << "Delete: " << pq.back() << endl;
                pq.pop_back();
            }
            //최솟값 삭제
            else {
                cout << "Delete: " << pq.front() << endl;
                pq.erase(pq.begin());
            }
        }
    }
    if (pq.empty()) {
        answer.push_back(0);
        answer.push_back(0);
    }
    else {
        answer.push_back(*max_element(pq.begin(), pq.end()));
        answer.push_back(*min_element(pq.begin(), pq.end()));
    }
    
    return answer;
}
```