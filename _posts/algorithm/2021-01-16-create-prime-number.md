---
title:  "프로그래머스 Lv.2 - 소수 만들기"
date:   2021-01-16 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [wintercoding]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12977

## 문제풀이
---

```cpp
#include <vector>
#include <iostream>
#include <algorithm>
using namespace std;

bool is_prime(int a) {
    if (a <= 1) return false;
    bool primeArr[a+1];
    for (int i = 0; i <= a; i++) {
        primeArr[i] = true;
    }
    for (int i = 2; i <= a; i++) {
        if (primeArr[i]) {
            for (int j = i*i; j <= a; j+=i) {
                primeArr[j] = false;
            }
        }   
    }
    return primeArr[a];
}

int solution(vector<int> nums) {
    int answer = 0;
    
    vector<int> temp;
    for (int i = 0; i < nums.size()-3; i++) {
        temp.push_back(0);
    }
    temp.push_back(1);
    temp.push_back(1);
    temp.push_back(1);   
    
    do {
        int sum = 0;
        for (int i = 0; i < temp.size(); i++) {
            if (temp[i] == 1) {
                sum += nums[i];
            }
        }
        if (is_prime(sum)) {
            answer++;
        }
    } while (next_permutation(temp.begin(), temp.end()));

    return answer;
}
```