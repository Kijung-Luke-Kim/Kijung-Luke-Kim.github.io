---
title:  "프로그래머스 Lv.3 - 브라이언의 고민"
date:   2021-02-03 09:00:00 +0900
author: Kijung Luke Kim
categories: [Algorithm, Programmers]
tags: [kakao]
image: /assets/img/posts/algorithm.png
---

## 문제 설명
---

> https://programmers.co.kr/learn/courses/30/lessons/1830

## 문제풀이
---

```cpp
#include <string>
#include<vector>
#include<memory.h>
#include<iostream>

#define SMALLWORD -1;
#define NOTHING 0;
#define JUSTWORD 1;
#define RULE1 2;
#define RULE2 3;
#define RULE12 4; 
using namespace std;

// 전역 변수를 정의할 경우 함수 내에 초기화 코드를 꼭 작성해주세요.
string solution(string sentence) {
    string answer = "";
    
    int use[26]={0,};// 사용횟수
    bool used[26]={false,}; // 사용되었는지 안됬는지
    int startpos[26]={0,}; //시작 위치
    int endpos[26]={0,}; //끝 위치
    int check[1001]={0,}; // 모든 단어를 벡터에 넣었는지 check // 소문자= -1,그냥 단어 1, 규칙1=2, 규칙2 =3 , 규칙1+2 = 4
    vector<int> alphapos; //소문자가 나타난 순서
    
    for(int i=0; i<sentence.size(); i++){
        if(islower(sentence[i])){
            use[sentence[i]-'a']++;
            if(used[sentence[i]-'a'] == false){
                used[sentence[i]-'a'] = true;
                startpos[sentence[i]-'a'] =  i;
                alphapos.push_back(sentence[i]-'a');
            }
        }
        if(sentence[i] == ' '){
            cout<<"space"<<endl;
            return "invalid";
        }
    }
    memset(used, false, sizeof(used));
    for(int i= sentence.size()-1; i>=0; i--){
        if(islower(sentence[i])){
            if(used[sentence[i]-'a']==false){
                used[sentence[i]-'a'] = true;
                endpos[sentence[i]-'a'] = i;
            }
        }
    }
    
    //// 여기서 부터 점검 및 저장
    vector<string> s;
    for(int i=0; i<alphapos.size(); i++){
        
        char now=alphapos[i]+'a';
        if(use[now-'a']==1||use[now-'a']>=3){ // 규칙 1.
            int nowstart = startpos[now-'a']-1;
            int nowend = endpos[now-'a']+1;
            if(nowstart<0||nowend>=sentence.size()||islower(sentence[nowstart])||islower(sentence[nowend])){
                cout<<"over index"<<endl;
                return "invalid";
            }
            
            string defaultword;
            for(int j=0; j<nowstart; j++){ // 그냥 단어
                if(check[j] == 0){
                    if(!isupper(sentence[j])){
                       cout<<"default word lower alpha"<<endl;
                        return "invalid";
                    }
                    defaultword.push_back(sentence[j]);
                    check[j]=JUSTWORD;
                }
            }
            if(defaultword.size()!=0){
                s.push_back(defaultword);
            }
            
            bool flag = true; // 대문자
            string rule1;
            if(check[nowstart]==2 ||check[nowend]==2){
                cout<<"double rule1"<<endl;
                return "invalid";
            }
            for(int j=nowstart; j<=nowend; j++ ){
                if(flag){ // 대문자
                    if(!isupper(sentence[j])){
                        cout<<"rule1 not Upper alpha"<<endl;
                        return "invalid";
                    }else{
                        if(check[j]!=3){
                            rule1.push_back(sentence[j]);
                            check[j]=RULE1;
                        }else{
                            check[j] = RULE12;
                        }
                        flag = false;
                    }
                }else{// 소문자
                    if(!islower(sentence[j])||now!=sentence[j]){
                        cout<<"rule1 not lower alpha"<<endl;
                        return "invalid";
                    }else{
                        check[j]=SMALLWORD;
                    }
                    flag = true;
                }
            }
            if(rule1.size()!=0){
                s.push_back(rule1);
            }
        }else if(use[now-'a']==2){ // 규칙2.
            string defaultword;
            
            for(int j=0; j<startpos[now-'a']; j++){ // 그냥 단어
                if(check[j] == 0){
                    if(!isupper(sentence[j])){
                        
                        cout<<"in rule2, default word lower alpha"<<endl;
                        return "invalid";
                    }
                    defaultword.push_back(sentence[j]);
                    check[j]=JUSTWORD;
                }
            }
            if(defaultword.size()!=0){
                s.push_back(defaultword);
            }
            
            
            
            if(check[startpos[now-'a']]!=0||check[endpos[now-'a']]!=0){ // aA bAb Aa 상황
                if(endpos[now-'a']-startpos[now-'a']==2){
                    continue;
                }
                cout<<"rule2, first and last alpha include another"<<endl;
                return "invalid";
            }
         
            check[startpos[now-'a']] = SMALLWORD;
            check[endpos[now-'a']] =SMALLWORD;
            
            int nowstart = startpos[now-'a']+1;
            int nowend = endpos[now-'a']-1;
            
            if(islower(sentence[nowstart])||islower(sentence[nowend])){
                cout<<"rule2, second alpha or second last alpha is lower alpha"<<endl;
                return "invalid";
            } 
            if(i!=alphapos.size()-1){
                char next = alphapos[i+1]+'a';
                if(startpos[next-'a']>=startpos[now-'a']&&startpos[next-'a']<=endpos[now-'a']){ // 규칙2와 1이 겹쳐있는 경우
                    if((endpos[now-'a']-startpos[now-'a'])-4 != endpos[next-'a']-startpos[next-'a']){
                        cout<<now<<endl;
                        cout<<"this can not be rule1, in rule2 "<<endl;
                        return "invalid";
                    }
                }
            }
            
            string rule2;
            for(int j=nowstart; j<=nowend; j++){
                if(isupper(sentence[j])){
                    rule2.push_back(sentence[j]);
                }
                check[j] = RULE2;
            }
            if(rule2.size()!=0){
                s.push_back(rule2);
            }
        }
    }
    
    
    //끝내고 answer에 푸쉬
    for(int i=0; i<s.size(); i++){
        for(int j=0; j<s[i].size(); j++){
            answer.push_back(s[i][j]);
        }
            answer.push_back(' ');
    }
    for(int i=0; i<sentence.size(); i++){
        if(check[i]==0){
            if(isupper(sentence[i])){
                answer.push_back(sentence[i]);
            }else{
                cout<<"last default word is Lower error"<<endl;
                return "invalid";
            }
        }
    }
    if(answer.back() == ' '){
        answer.pop_back();
    }
    if(answer.size() == 0){
        cout<<"answer size is 0 error"<<endl;
        return "invalid";
    }
    return answer;
}
```