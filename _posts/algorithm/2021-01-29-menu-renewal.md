---
title:  "프로그래머스 Lv.2 - 메뉴 리뉴얼"
date:   2021-01-29 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/72411

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <map>
#include <cstring>
#include <iostream>
#include <algorithm>
using namespace std;

map<string, int> menus;
bool selected[10] = { false, };

void DFS(string order, int idx, int cnt, int size) {
	if (cnt == size) {
		string comb;
		for (int i = 0; i < order.size(); i++) {
			if (selected[i]) comb += order[i];
		}
		menus[comb] += 1;
		return;
	}
	for (int i = idx; i < order.size(); i++) {
		if (selected[i]) continue;
		selected[i] = true;

		DFS(order, i, cnt + 1, size);

		selected[i] = false;
	}
}

vector<string> solution(vector<string> orders, vector<int> course) {
	vector<string> answer;
	map<int, int> maxSize;

	for (int i = 0; i < orders.size(); i++) {
		for (int j = 0; j < course.size(); j++) {
			if (course[j] > orders[i].size()) break;
			sort(orders[i].begin(), orders[i].end());
			DFS(orders[i], 0, 0, course[j]);
			memset(selected, false, 10 * sizeof(bool));
		}
	}

	for (auto menu = menus.begin(); menu != menus.end(); ++menu) {
		if (menu->second > 1 && menu->second > maxSize[menu->first.size()]) {
			maxSize[menu->first.size()] = menu->second;
		}
	}
	for (auto menu = menus.begin(); menu != menus.end(); ++menu) {
		if (menu->second == maxSize[menu->first.size()]) {
			answer.push_back(menu->first);
		}
	}

	return answer;
}
```