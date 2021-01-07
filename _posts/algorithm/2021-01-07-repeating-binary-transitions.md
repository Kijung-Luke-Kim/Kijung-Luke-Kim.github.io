---
title:  "프로그래머스 Lv.2 - 이진 변환 반복하기"
date:   2021-01-07 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [monthlycodingchallenge]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/70129

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

vector<int> solution(string s) {
    vector<int> answer;
    int countBin = 0;
    int countZero = 0;
        
    //이진변환
    while (s != "1") {
        string noZero = "";
         //0제거
        for (int i = 0; i < s.size(); i++) {
            if (s[i]=='1') {
                noZero += "1";
            }
            else {
                countZero++;
            }
        }
        s = noZero;
        
        int length = s.size();
        string temp = "";
        //길이를 이진법으로 변환
        while (true) {
            if (length <= 1) {
                temp += to_string(length);
                break;
            }
            int div = length % 2;
            temp += to_string(div);
            length /= 2;
        }
        reverse(temp.begin(), temp.end());
        s = temp;
        countBin++;
    }
    
    answer.push_back(countBin);
    answer.push_back(countZero);
   
    return answer;
}
```