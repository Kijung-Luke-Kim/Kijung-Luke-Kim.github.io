---
title:  "프로그래머스 Lv.3 - 베스트앨범"
date:   2021-02-18 08:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [hash]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42579

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <unordered_map>
#include <algorithm>

using namespace std;

bool cmp(pair<string, int> a, pair<string, int> b) {
    return a.second > b.second;
}

bool cmp_int(pair<int, int> a, pair<int, int> b){
    return a.second > b.second;
}

vector<int> solution(vector<string> genres, vector<int> plays) {
    vector<int> answer;
    unordered_map<string, int> genre_views;
    unordered_map<string, vector<pair<int, int>>> genre_music_views;
    
    vector<pair<string, int>> v_genre_views;
    
    for (int i = 0; i < genres.size(); i++) {
        genre_views[genres[i]] += plays[i];
        genre_music_views[genres[i]].push_back(make_pair(i, plays[i]));
    }
    
    v_genre_views.assign(genre_views.begin(), genre_views.end());
    sort(v_genre_views.begin(), v_genre_views.end(), cmp);
    
    for (auto &m : genre_music_views) {
        sort(m.second.begin(), m.second.end(), cmp_int);
    }
    
    for (int i = 0; i < v_genre_views.size(); i++) {
        answer.push_back(genre_music_views[v_genre_views[i].first][0].first);
        if (genre_music_views[v_genre_views[i].first].size() > 1) {
            answer.push_back(genre_music_views[v_genre_views[i].first][1].first);
        }
    }
    
    return answer;
}
```