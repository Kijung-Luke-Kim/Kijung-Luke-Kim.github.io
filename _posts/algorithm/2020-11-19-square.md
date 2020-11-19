---
title:  "프로그래머스 Lv.1 - 제일 작은 수 제거하기"
date:   2020-11-19 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12935

정수를 저장한 배열, arr 에서 가장 작은 수를 제거한 배열을 리턴하는 함수, solution을 완성해주세요. 단, 리턴하려는 배열이 빈 배열인 경우엔 배열에 -1을 채워 리턴하세요. 예를들어 arr이 [4,3,2,1]인 경우는 [4,3,2]를 리턴 하고, [10]면 [-1]을 리턴 합니다.

**제한 사항**   

- arr은 길이 1 이상인 배열입니다.
- 인덱스 i, j에 대해 i ≠ j이면 arr[i] ≠ arr[j] 입니다.

**입출력 예**

|s|return|
|---|---|
|[4,3,2,1]|[4,3,2]|
|[10]|[-1]|

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;
vector<int> solution(vector<int> arr) {
    vector<int> answer;
    if (arr.size() <= 1) {
        answer.push_back(-1);
        return answer;
    }
    int min = arr[0];
    auto saveIt = arr.begin();
    for (auto it = arr.begin(); it < arr.end(); ++it) {
        if (min > *it) {
            min = *it;
            saveIt = it;
        }
    }
    arr.erase(saveIt);
    answer = arr;
    return answer;
}
```
