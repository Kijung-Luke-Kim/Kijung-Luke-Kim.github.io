---
title:  "프로그래머스 Lv.2 - 쿼드압축 후 개수 세기"
date:   2020-12-29 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [monthlycodingchallenge]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/68936

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

void check(vector<vector<int>> arr, int &countZero, int &countOne) {
    int n = arr[0][0];
    bool isCompressed = true;
    for (int i = 0; i < arr.size(); i++) {
        for (int j = 0; j < arr.size(); j++) {
            if (arr[i][j] != n) {
                isCompressed = false;
                break;
            }
        }
        if (!isCompressed)
            break;
    }
    if (isCompressed) {
        switch (n) {
            case 0 :
                countZero++;
                break;
            case 1:
                countOne++;
                break;
        }
    }
    else {
        vector<vector<int>> LT;
        vector<vector<int>> LB;
        vector<vector<int>> RT;
        vector<vector<int>> RB;
        
        for (int i = 0; i < arr.size()/2; i++) {
            vector<int> L;
            vector<int> R;
            for (int j = 0; j < arr.size()/2; j++) {
                L.push_back(arr[i][j]);
            }
            for (int j = arr.size()/2; j < arr.size(); j++) {
                R.push_back(arr[i][j]);
            }
            LT.push_back(L);
            RT.push_back(R);
        }
        for (int i = arr.size()/2; i < arr.size(); i++) {
            vector<int> L;
            vector<int> R;
            for (int j = 0; j < arr.size()/2; j++) {
                L.push_back(arr[i][j]);
            }
            for (int j = arr.size()/2; j < arr.size(); j++) {
                R.push_back(arr[i][j]);
            }
            LB.push_back(L);
            RB.push_back(R);
        }
        check(LT, countZero, countOne);
        check(LB, countZero, countOne);
        check(RT, countZero, countOne);
        check(RB, countZero, countOne);
    }
}

vector<int> solution(vector<vector<int>> arr) {
    vector<int> answer;
    int countOne = 0;
    int countZero = 0;
    
    check(arr, countZero, countOne);
    
    answer.push_back(countZero);
    answer.push_back(countOne);
    
    return answer;
}
```