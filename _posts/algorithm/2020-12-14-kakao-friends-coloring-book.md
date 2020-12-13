---
title:  "프로그래머스 Lv.2 - 카카오 프렌즈 컬러링북"
date:   2020-12-14 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/1829

## 문제풀이
---

```cpp
#include <vector>
#include <queue>
#include <algorithm>

using namespace std;

vector<int> solution(int m, int n, vector<vector<int>> picture) {
    int number_of_area = 0;
    int max_size_of_one_area = 0;
    queue<pair<int, int>> q;
    bool visited[m][n];
    vector<int> areas;
    
    for (int i = 0; i < m; i++) {
        for (int j = 0; j < n; j++) {
            visited[i][j] = false;
        }
    }
    
    for (int i = 0; i < m; i++) {
        for (int j = 0; j < n; j++) {
            if (picture[i][j] != 0 && !visited[i][j]) {
                int area = 0;
                int color = picture[i][j];
                q.push(make_pair(i, j));
                visited[i][j] = true;
                while (!q.empty()) {
                    int y = q.front().first;
                    int x = q.front().second;
                    q.pop();
                    area++;
                    if (x+1 < n && picture[y][x+1] == color && !visited[y][x+1]) {
                        q.push(make_pair(y, x+1));
                        visited[y][x+1] = true;
                    }
                    if (x-1 >= 0 && picture[y][x-1] == color && !visited[y][x-1] ) {
                        q.push(make_pair(y, x-1));
                        visited[y][x-1] = true;
                    }
                    if (y+1 < m && picture[y+1][x] == color && !visited[y+1][x]) {
                        q.push(make_pair(y+1, x));
                        visited[y+1][x] = true;
                    }
                    if (y-1 >= 0 && picture[y-1][x] == color && !visited[y-1][x]) {
                        q.push(make_pair(y-1, x));
                        visited[y-1][x] = true;
                    }
                }
                areas.push_back(area);
            }
        }
    }
    
    number_of_area = areas.size();
    max_size_of_one_area = *max_element(areas.begin(), areas.end());
    vector<int> answer(2);
    answer[0] = number_of_area;
    answer[1] = max_size_of_one_area;
    return answer;
}
```