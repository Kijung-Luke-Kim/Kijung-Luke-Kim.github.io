---
layout: post
title:  "Forager 모작(8) - 오늘한일"
date:   2020-10-05T18:00:00+0900
author: Kijung Luke Kim
categories: [Project, Forager]
tags: [game, forager]
image: /assets/img/posts/forager.jpg
---

## 1. 맵 클래스 수정
---

- 오브젝트 객체 추가
> *earth.h* : 아이템, 빌딩 등을 담을 유닛 벡터를 추가하고 게임 시작시 맵을 초기화할 다양한 함수들을 추가했다.
```cpp
class earth : public gamemap
{
private:
	vector<tile> _vTile;
	vector<unit> _vUnit;        //아이템, 빌딩 <- 충돌용 유닛 벡터!
private:
	image* watertile;
	image* plaintile;
	image* plainedge;
	image* wave;
	image* underwater;
	int _count;
	int _frameCount;
	int wavetick;
public:
	HRESULT init();
	void release();
	void update();
	void render(HDC hdc);
	void mapSetup();            //오늘 작업한 내용!
	void setRandomObject();     //오늘 작업한 내용!
	float getResRatio();        //오늘 작업한 내용!
	int getPlayerPos();         //오늘 작업한 내용!
};
```
- 충돌 처리 코드 추가 (진행중)


## 2. 오브젝트 클래스 재설계
---

- 아이템 및 각종 오브젝트 기존 코드를 새로 설계한 구조에 맞춰 재작업.
> *resource.cpp*: earth.cpp의 타일맵에 랜덤하게 자원 오브젝트를 생성해주는 함수
```cpp
void resource::setRandomRes(RECT _rc)
{
	this->rc = _rc;
	this->layer = LAYER::OBJECT;
	this->tag = TAG::OBJECT;
	switch (RANDOM->range(NUMRES)) {
	case 0:
		this->objKey = "berry";
		this->objFrameX = 0;
		this->objFrameY = 0;
		this->hp = BERRYHP;
		break;
	case 1:
		this->objKey = "rock";
		this->objFrameX = 0;
		this->objFrameY = 0;
		this->hp = ROCKHP;
		break;
	case 2:
		this->objKey = "tree";
		this->objFrameX = 0;
		this->objFrameY = 0;
		this->hp = TREEHP;
		break;
	}
}
```
> 대부분 기존에 짜뒀던 맵툴 코드를 게임 구현을 위해 재설계한 구조에 맞춰 변경하는 작업을 진행중이다.

## 3. 코드 통합 및 카메라 매니저 작업
---


어느 정도 통합이 진행됐지만, 역시나 기존에 기능했던 기능이 대부분 설계없이 무분별하게 작성되었던 만큼,
내일까진 대부분의 작업이 기존 코드를 새로운 설계에 맞춰 작동시키는데 초점을 맞춰야 할것이다.



## 4. 그외 개인 블로그 활동
---


깃허브 블로그에 대한 환상(?)이 조금씩 깨지는 중. 부족한 시간을 쪼개 기초적인 마크다운 언어를 공부하고 있는데, 역시 상용 서비스에 비해선 여러모로 불편한 것이 사실이다.

아직까진 포스트 내용이 부실하지만 점차 보완해나갈 예정. 이미지나 이런 저런 내용들을 직접 꾸며나가야 하기에, 앞으로 틈틈히 짬을 내 이전 포스트 내용들도 수정해나가야 할듯 싶다.