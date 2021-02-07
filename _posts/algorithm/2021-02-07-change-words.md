---
title:  "프로그래머스 Lv.3 - 단어 변환"
date:   2021-02-07 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [bfs]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/43163

## 문제풀이
---

```cpp
#include <iostream>
#include <string>
#include <vector>
#include <queue>
#include <algorithm>

using namespace std;

bool isNear(string a, string b) {
    int count = 0;
    for (int i = 0; i < a.size(); i++) {
        if (a[i] != b[i])
            count++;
        if (count > 1) {
            return false;
        }
    }
    return true;
}

int BFS(string begin, string target, vector<string> words) {
    queue<pair<string, int>> q;
    vector<bool> visited (words.size(), false);
    
    //목표 단어가 없을시 종료
    if (find(words.begin(), words.end(), target) == words.end()) {
        return 0;
    }
    
    q.push(make_pair(begin, 0));
    while (!q.empty()) {
        string word = q.front().first;
        int distance = q.front().second;
        q.pop();
        //테스트용 출력코드
        //cout << word << " " << distance << endl;
        for (int i = 0; i < words.size(); i++) {
            if (!visited[i] && isNear(word, words[i])) {
                if (words[i] == target)
                    return distance+1;
                visited[i] = true;
                q.push(make_pair(words[i], distance+1));
            }
        }
    }
}

int solution(string begin, string target, vector<string> words) {
    int answer = 0;
    answer = BFS(begin, target, words);
    return answer;
}
```