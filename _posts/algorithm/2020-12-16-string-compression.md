---
title:  "프로그래머스 Lv.2 - 문자열 압축"
date:   2020-12-16 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/60057

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

int solution(string s) {
    int answer = 0;
    vector<int> lengthlist;
    for (int i = 1; i < s.size()+1; i++) {
        string comps = "";
        int pos = 0;
        int count = 1;
        while (pos < s.size()) {
            if (pos+count*i <= s.size()) {
                if (s.substr(pos, i) == s.substr(pos+count*i, i)) {
                    count++;
                }
                else {
                    if (count > 1) {
                        comps += to_string(count) + s.substr(pos, i);
                        pos += count*i;
                        count = 1;
                    }
                    else {
                        comps += s.substr(pos, i);
                        pos += i;
                    }
                }
            }
            else {
                comps += s.substr(pos, i);
                break;
            }            
        }
        int length = comps.size();
        lengthlist.push_back(length);
    }
    answer = *min_element(lengthlist.begin(), lengthlist.end());
    return answer;
}
```