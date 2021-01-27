---
title:  "프로그래머스 Lv.2 - [3차] 파일명 정렬"
date:   2021-01-27 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/17686

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <sstream>
#include <map>
#include <algorithm>
#include <iostream>

using namespace std;

bool comp(vector<string> a, vector<string> b) {
    transform(a[0].begin(), a[0].end(), a[0].begin(), ::toupper);
    transform(b[0].begin(), b[0].end(), b[0].begin(), ::toupper);
    if (a[0] == b[0]) {    
        return stoi(a[1]) < stoi(b[1]);  
    } 
    return a[0] < b[0];
}

vector<string> solution(vector<string> files) {
    vector<string> answer;
    vector<vector<string>> tokens;
    for (int i = 0; i < files.size(); i++) {
        string head = "";
        string number = "";
        string tail = "";
        stringstream ss(files[i]);
        vector<string> token;
        for (int j = 0; j < files[i].size(); j++) {
            if (files[i][j] <= '9' && files[i][j] >= '0') {
                getline(ss, head, files[i][j]);
                for (int k = j; k < files[i].size(); k++) {
                    if (k == files[i].size()-1) {
                        getline(ss, number);
                        number = files[i][j] + number;
                        break;
                    }
                   if (files[i][k] > '9' || files[i][k] < '0') {
                        getline(ss, number, files[i][k]);
                        number = files[i][j] + number;
                        getline(ss, tail);
                        tail = files[i][k] + tail;
                        break;
                    }
                }
                break;
            }
        }
        //cout << head << " " << number << " " << tail << endl;
        token.push_back(head);
        token.push_back(number);
        token.push_back(tail);
        token.push_back(files[i]);
        tokens.push_back(token);
    }
    stable_sort(tokens.begin(), tokens.end(), comp);
    for (auto token : tokens) {
        answer.push_back(token[3]);
    }
    return answer;
}
```