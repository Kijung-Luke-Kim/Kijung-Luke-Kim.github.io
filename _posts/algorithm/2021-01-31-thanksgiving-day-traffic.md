---
title:  "프로그래머스 Lv.3 - [1차] 추석 트래픽"
date:   2021-01-31 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/17676

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <sstream>
#include <iostream>

using namespace std;

int solution(vector<string> lines) {
    int answer = 0;
    vector<vector<string>> data;
    int traffic[24*60*60*1000 + 1] = { 0, };
    for (int i = 0; i < lines.size(); i++) {
        stringstream ss(lines[i]);
        string buf;
        vector<string> line;
        while(getline(ss, buf, ' ')) {
            line.push_back(buf);
        }
        data.push_back(line);
    }
    for (int i = 0; i < data.size(); i++) {
        stringstream ss(data[i][1]);
        string buf;
        float hour, min, sec;
        getline(ss, buf, ':');
        hour = stof(buf)*60*60*1000;
        getline(ss, buf, ':');
        min = stof(buf)*60*1000;
        getline(ss, buf, ':');
        sec = stof(buf)*1000;
        int time = hour + min + sec;
        data[i][2].pop_back();
        int proctime = (stof(data[i][2])*1000);
        int endtime = time + 999;
        int starttime = time - proctime + 1;
        starttime = starttime < 0 ? 0 : starttime;
        endtime = endtime > 24*60*60*1000 ? 24*60*60*1000 : endtime;
        cout << starttime << " " << proctime << " " << endtime << endl;
        for (int i = starttime; i <= endtime; i++) {
            traffic[i]++;
        }
    }
    for (int i = 0; i <= 24*60*60*1000; i++) {
        if (answer < traffic[i]) answer = traffic[i];
    }
    
    return answer;
}
```