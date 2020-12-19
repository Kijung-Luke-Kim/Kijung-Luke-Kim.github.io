---
title:  "프로그래머스 Lv.2 - 소수 찾기"
date:   2020-12-19 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [exhaustivesearch]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42839

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>
#include <iostream>

using namespace std;

int solution(string numbers) {
    int answer = 0;
    sort(numbers.begin(), numbers.end(), greater<int>());
    vector<bool> is_prime;
    int number = stoi(numbers);
    for (int i = 0; i <= number; i++) {
        if (i < 2) {
            is_prime.push_back(false);
        }
        else {
            is_prime.push_back(true);
        }
    }
    for (int i = 2; i*i <= number; i++) {
        if (is_prime[i]) {
            for (int j = i*i; j <= number; j+= i) {
                *(is_prime.begin()+j) = false;
            }
        }
    }
    for (int i = 0; i <= number; i++) {
        if (is_prime[i]) {
            string temp;
            temp = numbers;
            string snum = to_string(i);
            bool ispart = false;
            for (int j = 0; j < snum.size(); j++) {
                if (temp.find(snum[j]) != string::npos) {
                    temp.erase(temp.find(snum[j]), 1);
                    ispart = true;
                }
                else {
                    ispart = false;
                    break;
                }
            }
            if (ispart==true) {
                answer++;
            }
        }
    }
    return answer;
}
```