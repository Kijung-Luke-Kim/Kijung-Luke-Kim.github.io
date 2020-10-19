---
layout: post
title:  "Forager 모작(10) - 오늘한일"
date:   2020-10-06T20:00:00+0900
author: Kijung Luke Kim
categories: [Project, Forager]
tags: [game, forager]
image: /assets/img/posts/forager.jpg
---

## 1. 건물 클래스 수정
---

- 타일맵 상에 건물을 추가하는 기능을 새로운 클래스로 추가한다. *(진행중)*

> 설치가 불가능한 타일(바다, 장애물, 이미 건물이 존재하는 타일 등)에선 아래가 빨갛게 표시된다.

![20201006-1.png](/assets/img/posts/20201006-1.PNG)

> 반대로 설치가 가능한 타일 위에선 초록색이 표시되며 건물이 추가 가능하다.

![20201006-2.png](/assets/img/posts/20201006-2.PNG)

- 가능하면 다중타일 빌딩도 추가한다. *(진행중)*
  - 아직까진 맵툴 코드 발표 당시 추가 가능했던 싱글 타일 크기의 용광로 이외엔 구현하지 못했다. 이전 코드를 그대로 가져와서 쓰면 가능할 줄 알았으나 설계 자체가 변경되면서 아예 새로 작업을 해야하는 만큼 당초 예상보다 작업량이 늘어났다.
  - 설계없는 막코딩의 문제점을 다시금 체감하게 된 것으로 위안을 삼아야 할듯 싶다.

## 2. 토지 구입 기능 추가
---

- 이젠 기존의 맵툴 코드서 텍스쳐를 확장하는 기능을 제거 *(완료!)*
-  원작 게임과 동일하게 골드를 모으면 인근 토지를 구입할 수 있도록 만든다. (진행중)
- 섬 생성 함수화 *(완료!)*

> 이젠 아래 함수를 통해 주어진 x,y 좌표에 따라 맵생성이 가능하며, 더 이상 섬의 형태가 정사각형이 아니라 50%의 확률로 섬의 테두리에 위치한 타일들이 바다로 변경됨으로써 좀 더 자연스러운 형태를 띄게 되었다. 

![20201006-3.png](/assets/img/posts/20201006-3.PNG)

``` cpp
void earth::setIsland(int x, int y)
{
	for (int i = 0; i < TILEY; i++) {
		for (int j = 0; j < TILEX; j++) {
			if (j == 0 || j == TILEX - 1 || i == 0 || i == TILEY -1 ) {
				switch (RANDOM->range(2)) {
				case 0:
					_vTile[(y * MAPTILEY*TILEY + i * MAPTILEY) + x * TILEX + j].terrKey = "plaintile";
					_vTile[(y * MAPTILEY*TILEY + i * MAPTILEY) + x * TILEX + j].terrainFrameX = RANDOM->range(4);
					break;
				case 1:
					break;
				}
			}
			else {
				_vTile[(y * MAPTILEY*TILEY + i * MAPTILEY) + x * TILEX + j].terrKey = "plaintile";
				_vTile[(y * MAPTILEY*TILEY + i * MAPTILEY) + x * TILEX + j].terrainFrameX = RANDOM->range(4);
			}
		}
	}
}
```



## 3. 기존 블로그 게시물 수정
---

- 그간 마크다운 언어가 익숙치 않아 볼품없이 꾸며졌던 포스트 글도 하나씩 수정한다. (진행중)
  - 파일명 빌드 오류로 인해 과거 게시된 포스트들이 확인조차 불가능했던 버그를 이제서야 발견해 수정했다. 매번 푸시하고 나면 빌드에 걸리는 시간을 기다린 후에야 확인이 가능하단 점이 매우 불편하다. 장기적으론 자체 서버를 구축하는 대안도 고려해봐야 할듯 싶다.