---
title:  "프로그래머스 Lv.1 - 직사각형 별찍기"
date:   2020-12-01 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12969

## 문제풀이
---

```cpp
#include <iostream>

using namespace std;

int main(void) {
    int a;
    int b;
    cin >> a >> b;
    for (int i = 0; i < b; i++) {
        for(int j = 0; j < a; j++) {
            cout<<"*";
        }
        cout<<endl;
    }
    return 0;
}
```
