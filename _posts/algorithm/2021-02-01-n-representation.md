---
title:  "프로그래머스 Lv.3 - N으로 표현"
date:   2021-02-01 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [dp]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/42895

## 문제풀이
---

```cpp
// 문제가 개편되었습니다. 이로 인해 함수 구성이나 테스트케이스가 변경되어, 과거의 코드는 동작하지 않을 수 있습니다.
// 새로운 함수 구성을 적용하려면 [코드 초기화] 버튼을 누르세요. 단, [코드 초기화] 버튼을 누르면 작성 중인 코드는 사라집니다.
#include <string>
#include <vector>
#include <set>

using namespace std;

int answer = 9;
 
void dfs(int N, int number, int count, int currentNumber) {
    //일정횟수 이상갔다면 리턴
    if (count >= 9)        return;
    //현재수가 number와 같다면 작은횟수를 answer에 저장후 리턴
    if (currentNumber == number) {
        answer = min(answer, count);
        return;
    }
    int tempNumber = 0;
    //최대 N의 사용횟수는 9번까지이므로 이때까지 반복
    for (int i = 0; i + count< 9 ; i++) {
        //N부터 NN,NNN,NNNN .....
        tempNumber = tempNumber * 10 + N;
        //더하기 빼기 곱하기 나누기 dfs 사용
        dfs(N, number, count + 1 + i, currentNumber + tempNumber);
        dfs(N, number, count + 1 + i, currentNumber - tempNumber);
        dfs(N, number, count + 1 + i, currentNumber * tempNumber);
        dfs(N, number, count + 1 + i, currentNumber / tempNumber);
    }
}
 
int solution(int N, int number) {
    dfs(N, number, 0, 0);
    //answer가 9라는 뜻은 number와 맞는 경우가 없었던 것이므로 -1 리턴
    if (answer == 9)    return -1;
    return answer;
}
```