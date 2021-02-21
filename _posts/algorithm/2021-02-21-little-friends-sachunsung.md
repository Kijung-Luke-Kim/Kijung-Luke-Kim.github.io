---
title:  "프로그래머스 Lv.3 - 리틀 프렌즈 사천성"
date:   2021-02-21 08:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/1836

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <set>
#include <queue>

using namespace std;

struct tilePos {
    int x;
    int y;
    int turnCount;
    int direction; // 0 - vertical, 1 - horizontal
};

bool Safe(int x, int y, int maxX, int maxY) {
    if (x < 0 || x >= maxX) return false;
    if (y < 0 || y >= maxY) return false;
    return true;
}

bool CanRemove(char tile, vector<string> board) {
    tilePos startTile;
    queue<tilePos> q;
    vector<vector<bool>> visited (board.size(), vector<bool>(board[0].size(), false));
    for (int i = 0; i < board.size(); i++) {
        int found = board[i].find(tile);
        if (found != string::npos) {
            startTile.x = found;
            startTile.y = i;
            startTile.turnCount = 0;
            board[i][found] = '.';
            break;
        }
    }
    if (Safe(startTile.x+1, startTile.y, board[0].size(), board.size()) && 
        !visited[startTile.y][startTile.x+1] && 
        (board[startTile.y][startTile.x+1] == '.' || board[startTile.y][startTile.x+1] == tile)) {
        tilePos temp = startTile;
        temp.x += 1;
        temp.direction = 1;
        q.push(temp);
    }
    if (Safe(startTile.x-1, startTile.y, board[0].size(), board.size()) && 
        !visited[startTile.y][startTile.x-1] && 
        (board[startTile.y][startTile.x-1] == '.' || board[startTile.y][startTile.x-1] == tile)) {
        tilePos temp = startTile;
        temp.x -= 1;
        temp.direction = 1;
        q.push(temp);
    }
    if (Safe(startTile.x, startTile.y+1, board[0].size(), board.size()) && 
        !visited[startTile.y+1][startTile.x] && 
        (board[startTile.y+1][startTile.x] == '.' || board[startTile.y+1][startTile.x] == tile)) {
        tilePos temp = startTile;
        temp.y += 1;
        temp.direction = 0;
        q.push(temp);
    }
    if (Safe(startTile.x, startTile.y-1, board[0].size(), board.size()) && 
        !visited[startTile.y-1][startTile.x] && 
        (board[startTile.y-1][startTile.x] == '.' || board[startTile.y-1][startTile.x] == tile)) {
        tilePos temp = startTile;
        temp.y -= 1;
        temp.direction = 0;
        q.push(temp);
    }
    while (!q.empty()) {
        tilePos current = q.front();
        q.pop();
        visited[current.y][current.x] = true;
        if (current.turnCount > 1)
            continue;
        if (board[current.y][current.x] == tile)
            return true;
        if (Safe(current.x+1, current.y, board[0].size(), board.size()) && 
        !visited[current.y][current.x+1] && 
        (board[current.y][current.x+1] == '.' || board[current.y][current.x+1] == tile)) {
            tilePos temp = current;
            temp.x += 1;
            temp.direction = 1;
            if (current.direction == 0)
                temp.turnCount += 1;
            q.push(temp);
        }
        if (Safe(current.x-1, current.y, board[0].size(), board.size()) && 
            !visited[current.y][current.x-1] && 
            (board[current.y][current.x-1] == '.' || board[current.y][current.x-1] == tile)) {
            tilePos temp = current;
            temp.x -= 1;
            temp.direction = 1;
            if (current.direction == 0)
                temp.turnCount += 1;
            q.push(temp);
        }
        if (Safe(current.x, current.y+1, board[0].size(), board.size()) && 
            !visited[current.y+1][current.x] && 
            (board[current.y+1][current.x] == '.' || board[current.y+1][current.x] == tile)) {
            tilePos temp = current;
            temp.y += 1;
            temp.direction = 0;
            if (current.direction == 1)
                temp.turnCount += 1;
            q.push(temp);
        }
        if (Safe(current.x, current.y-1, board[0].size(), board.size()) && 
            !visited[current.y-1][current.x] && 
            (board[current.y-1][current.x] == '.' || board[current.y-1][current.x] == tile)) {
            tilePos temp = current;
            temp.y -= 1;
            temp.direction = 0;
            if (current.direction == 1)
                temp.turnCount += 1;
            q.push(temp);
        }
    }
    return false;
}
void RemoveTile(char tile, vector<string> &board) {
    for (int i = 0; i < board.size(); i++) {
        for (int j = 0; j < board[i].size(); j++) {
            if (board[i][j] == tile)
                board[i][j] = '.';
        }
    }
}
string solution(int m, int n, vector<string> board) {
    string answer = "";
    set<char> tiles;
    for (auto row : board) {
        for (auto tile : row) {
            if (isalpha(tile))
                tiles.insert(tile);
        }
    }
    while (!tiles.empty()) {
        bool removed = false;
        auto iter = tiles.begin();
        while (iter != tiles.end()) {
            if (CanRemove(*iter, board)) {
                RemoveTile(*iter, board);
                answer += *iter;
                removed = true;
                tiles.erase(iter);
                break;
            }
            else
                ++iter;
        }
        if (!removed) {
            answer = "IMPOSSIBLE";
            break;
        }
    }
    return answer;
}
```