---
title:  "프로그래머스 Lv.2 - 후보키"
date:   2021-01-24 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42890

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <set>
#include <iostream>

using namespace std;

int solution(vector<vector<string>> relation) {
    int answer = 0;
    int n = relation[0].size();
    string cols = "12345678";
    vector <string> keys;

    //컬럼 조합
    for (int k = 1; k <= n; k++) {
        string key = "";
        for (int i = 0; i < n-k; i++) {
            key.push_back('0');
        }
        for (int i = 0; i < k; i++) {
            key.push_back('1');
        }
        do {
            string candKey = "";
            for (int i = 0; i < key.size(); i++) {
                if (key[i] == '1') {
                    candKey.push_back(cols[i]);
                }
            }
            keys.push_back(candKey);
        } while (next_permutation(key.begin(), key.end()));
    }
    
    //후보키 확인
     while (true) {
        bool isPop = false;
        for (auto key : keys) {
            set<string> data;
            bool isCand;
            for (auto row : relation) {
                string sKey = "";
                for (int i = 0; i < key.size(); i++) {
                    sKey.append(row[key[i] - '0'-1]);
                    //cout << row[key[i] - '0' - 1] << endl;
                }
                auto ret = data.insert(sKey);
                if (!ret.second) {
                    isCand = false;
                    break;
                }
                isCand = true;
            }
            if (isCand) {
                isPop = true;
                answer++;
                //cout << "key : " << key << endl;
                //최소성 제거
                auto it = keys.begin();
                while (it != keys.end()) {
                    if (includes(it->begin(), it->end(), key.begin(), key.end())) {
                        //cout << *it << endl;
                        keys.erase(it);
                    }
                    else {
                        ++it;
                    }
                }
                break;
            }
        }
        if (!isPop) break;
    }
    return answer;
}
```