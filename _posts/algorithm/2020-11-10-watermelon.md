---
title:  "프로그래머스 Lv.1 - 수박수박수박수박수박수?"
date:   2020-11-10 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers, Level1]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12922

길이가 n이고, 수박수박수박수....와 같은 패턴을 유지하는 문자열을 리턴하는 함수, solution을 완성하세요. 예를들어 n이 4이면 수박수박을 리턴하고 3이라면 수박수를 리턴하면 됩니다.

**제한 사항**   

- n은 길이 10,000이하인 자연수입니다.

<br>

**입출력 예**

|n|result|
|---|---|
|3|"수박수"|
|4|"수박수박"|

<br>

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

string solution(int n) {
    string answer = "";
    for (int i = 0; i < n; i++) {
        if (i % 2 == 0) {
            answer += "수";
        }
        else {
            answer += "박";
        }
    }
    return answer;
}
```
