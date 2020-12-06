---
title:  "프로그래머스 Lv.1 - 자연수 뒤집어 배열로 만들기"
date:   2020-11-16 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers, Level1]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12932

자연수 n을 뒤집어 각 자리 숫자를 원소로 가지는 배열 형태로 리턴해주세요. 예를들어 n이 12345이면 [5,4,3,2,1]을 리턴합니다.

**제한 사항**   

- n은 10,000,000,000이하인 자연수입니다.

**입출력 예**

|s|return|
|---|---|
|12345|[5,4,3,2,1]|

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

vector<int> solution(long long n) {
    vector<int> answer;
    string strn = to_string(n);
    for (int i = 0; i < strn.length();i++) {
        answer.push_back(strn[i]-'0');
    }
    reverse(answer.begin(), answer.end());
    return answer;
}
```
