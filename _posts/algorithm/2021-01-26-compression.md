---
title:  "프로그래머스 Lv.2 - [3차] 압축"
date:   2021-01-26 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/17684

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <map>

using namespace std;

vector<int> solution(string msg) {
    vector<int> answer;
    map<string, int> dictionary;
    for (auto i = 'A'; i <= 'Z'; i++) {
        string word = "";
        word.push_back(i);
        dictionary.insert(make_pair(word, dictionary.size()+1));
    }
    string word = msg;
    while (word.size() > 0) {
        for (int i = word.size(); i > 0; i--) {
            string curIn = word.substr(0, i);
            auto result = dictionary.find(curIn);
            if (result != dictionary.end()) {
                answer.push_back(result->second);
                word.erase(0, i);            
                if (word.size() > 0) {
                    auto nextWord = curIn+word[0];
                    dictionary.insert(make_pair(nextWord, dictionary.size()+1));
                }
                break;
            }
        }
    }
    return answer;
}
```