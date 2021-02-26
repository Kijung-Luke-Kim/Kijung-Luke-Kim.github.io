---
title:  "프로그래머스 Lv.3 - 방문 길이"
date:   2021-02-26 08:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao, simulation]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/49994

## 문제풀이
---

```cpp
#include <string>
using namespace std;

bool paths[11][11][11][11] = { false, };
bool MAP[11][11] = { false, };

struct Pos {
	int x;
	int y;
};

int solution(string dirs) {
    int answer = 0;

	Pos currPos, nextPos;
	currPos.x = 0;
	currPos.y = 0;

    for (int i = 0; i < dirs.size(); i++) {
        if (dirs[i] == 'U') {
			if (currPos.y < 5) {
				nextPos.x = currPos.x;
				nextPos.y = currPos.y + 1;
				if (!paths[currPos.x+5][currPos.y+5][nextPos.x+5][nextPos.y+5])  {
					paths[currPos.x+5][currPos.y+5][nextPos.x+5][nextPos.y+5] = true;
					paths[nextPos.x+5][nextPos.y+5][currPos.x+5][currPos.y+5] = true;
					answer++;
				}
				currPos.y++;
			}
		}
		else if (dirs[i] == 'D') {
			if (currPos.y > -5) {
				nextPos.x = currPos.x;
				nextPos.y = currPos.y - 1;
				if (!paths[currPos.x+5][currPos.y+5][nextPos.x+5][nextPos.y+5])  {
					paths[currPos.x+5][currPos.y+5][nextPos.x+5][nextPos.y+5] = true;
					paths[nextPos.x+5][nextPos.y+5][currPos.x+5][currPos.y+5] = true;
					answer++;
				}
				currPos.y--;
			}
		}
		else if (dirs[i] == 'R') {
			if (currPos.x < 5) {
				nextPos.x = currPos.x + 1;
				nextPos.y = currPos.y;
				if (!paths[currPos.x+5][currPos.y+5][nextPos.x+5][nextPos.y+5])  {
					paths[currPos.x+5][currPos.y+5][nextPos.x+5][nextPos.y+5] = true;
					paths[nextPos.x+5][nextPos.y+5][currPos.x+5][currPos.y+5] = true;
					answer++;
				}
				currPos.x++;
			}
		}
		else if (dirs[i] == 'L') {
			if (currPos.x > -5) {
				nextPos.x = currPos.x - 1;
				nextPos.y = currPos.y;
				if (!paths[currPos.x+5][currPos.y+5][nextPos.x+5][nextPos.y+5])  {
					paths[currPos.x+5][currPos.y+5][nextPos.x+5][nextPos.y+5] = true;
					paths[nextPos.x+5][nextPos.y+5][currPos.x+5][currPos.y+5] = true;
					answer++;
				}
				currPos.x--;
			}
		}
    }
    
    return answer;
}
```