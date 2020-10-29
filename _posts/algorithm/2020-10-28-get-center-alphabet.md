---
title:  "프로그래머스 Lv.1 - 가운데 글자 가져오기"
date:   2020-10-28 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12903

<!-- 단어 s의 가운데 글자를 반환하는 함수, solution을 만들어 보세요. 단어의 길이가 짝수라면 가운데 두글자를 반환하면 됩니다.

**제한사항**

---

- s는 길이가 1 이상, 100이하인 스트링입니다.

**입출력 예**

---

|s|return|
|---|---|
|"abcde"|"c"|
|"qwer"|"we"| -->

## 문제풀이
---

```cpp
#include <string>
#include <vector>

using namespace std;

string solution(string s) {
    string answer = "";
    //홀수
    if (s.length() % 2 == 1) {
        answer = s[int(s.length()/2)];
    }
    else {
        answer += s[int(s.length()/2 - 1)];
        answer += s[int(s.length()/2)];

    }
    return answer;
}
```
