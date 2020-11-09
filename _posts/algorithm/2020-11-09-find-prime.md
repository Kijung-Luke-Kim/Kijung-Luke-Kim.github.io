---
title:  "프로그래머스 Lv.1 - 소수 찾기"
date:   2020-11-09 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [practice]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/12921

1부터 입력받은 숫자 n 사이에 있는 소수의 개수를 반환하는 함수, solution을 만들어 보세요.

소수는 1과 자기 자신으로만 나누어지는 수를 의미합니다.
(1은 소수가 아닙니다.)

**제한 사항**   

- n은 2이상 1000000이하의 자연수입니다.

<br>

**입출력 예**

|n|result|
|---|---|
|10|4|
|5|3|

<br>

## 문제풀이
---

```cpp
#include <string>
#include <vector>
#include <algorithm>

using namespace std;

int solution(int n) {
    long count = 0;
   // n=100;
    if (n <= 1) return count;
    
    bool* PrimeArray = new bool[n + 1];
    
    for (int i = 2; i <= n; i++)
	    PrimeArray[i] = true;
    
    for (long i = 2; i * i <= n; i++)
	{
		if (PrimeArray[i])
			for (long j = i * i; j <= n; j += i)
			    PrimeArray[j] = false;
	}
    for (long i = 2; i <= n; i++) {
        if (PrimeArray[i] == true) {
            count++;
        }
    }
    return count;
}
```
