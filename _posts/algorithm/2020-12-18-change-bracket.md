---
title:  "프로그래머스 Lv.2 - 괄호 변환"
date:   2020-12-18 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/60058

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <iostream>

using namespace std;

bool is_balanced(string str) {
    int count1 = 0;
    int count2 = 0;
    for (int i = 0; i < str.size(); i++) {
        if (str[i] == '(') {
            count1++;
        }
        else if (str[i] == ')') {
            count2++;
        }
    }
    return (count1 == count2);
}

bool is_right(string str) {
    vector<char> charstack;
    for (int i = 0; i < str.size(); i++) {
        if (str[i] == ')') {
            if (charstack.size() == 0) {
                return false;
            }
            else {
                charstack.pop_back();
            }
        }
        else {
            charstack.push_back('(');
        }
    }
    return (charstack.size() == 0);
}

string makeright(string str) {
    string rightstr = "";
    // string u;
    // string v;
    if (str.size() == 0) {
        return rightstr;
    }
    else {
        for (int i = 2; i <= str.size(); i+=2) {
            string u = str.substr(0, i);
            string v = str.substr(i, str.size());
            if (is_balanced(u) && is_balanced(v)) {
                cout << u << endl;
                if (is_right(u)) {
                    rightstr = u+makeright(v);
                    return rightstr;
                }
                else {
                    rightstr.insert(0, "(");
                    rightstr += makeright(v);
                    rightstr.append(")");
                    u.erase(u.begin());
                    u.pop_back();
                    for (int i = 0; i < u.size(); i++) {
                        if (u[i] == '(') {
                            u.replace(i, 1, ")");
                        }
                        else if (u[i] == ')') {
                            u.replace(i, 1, "(");
                        }
                    }
                    rightstr += u;
                    return rightstr;
                }
                break;
            }
        }
    }
    return rightstr;
}

string solution(string p) {
    string answer = "";
    if (is_right(p)) {
        answer = p;
    }
    else {
        answer = makeright(p);
    }
    return answer;
}
```