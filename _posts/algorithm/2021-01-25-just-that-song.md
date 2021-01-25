---
title:  "프로그래머스 Lv.2 - [3차] 방금그곡"
date:   2021-01-25 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/17683

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <sstream>

using namespace std;

string solution(string m, vector<string> musicinfos) {
    string answer = "";
    vector<vector<string>> infos;
    vector<pair<int, string>> answers;
    for (int i = 0; i < m.size(); i++) {
        if (m[i] == '#') {
            m[i-1] = tolower(m[i-1]);
            m.erase(i, 1);
        }
    }
    //문자열 토큰화
    for (auto info : musicinfos) {
        vector<string> infotokens;
        stringstream ss(info);
        string buf;
        while (getline(ss, buf, ',')) {
            infotokens.push_back(buf);
        }
        for (int i = 0; i < infotokens[3].size(); i++) {
            if (infotokens[3][i] == '#') {
                infotokens[3][i-1] = tolower(infotokens[3][i-1]);
                infotokens[3].erase(i, 1);
            }
        }
        infos.push_back(infotokens);
    }
    for (auto info : infos) {
        string stimehr = "";
        stimehr.push_back(*(info[0].begin()));
        stimehr.push_back(*(info[0].begin()+1));
        string etimehr = "";
        etimehr.push_back(*(info[1].begin()));
        etimehr.push_back(*(info[1].begin()+1));
        string stimemin = "";
        stimemin.push_back(*(info[0].end()-2));
        stimemin.push_back(*(info[0].end()-1));
        string etimemin = "";
        etimemin.push_back(*(info[1].end()-2));
        etimemin.push_back(*(info[1].end()-1));
        int time;
        time = 60*(stoi(etimehr)-stoi(stimehr)) + (stoi(etimemin) - stoi(stimemin))*1;
        string lyric = "";
        for (int i = 0; i < time; i++) {
            lyric.push_back(info[3][i%info[3].size()]);
        }
        if (lyric.find(m) != string::npos) {
            answers.push_back(make_pair(time, info[2]));
        }
    }
    if (answers.size() > 0) {
        auto max = max_element(answers.begin(), answers.end())->first;
        for (auto it = answers.begin(); it < answers.end(); ++it) {
            if (it->first == max) {
                answer = it->second;
                break;
            }
        }
    }
    else answer = "(None)";
    return answer;
}
```