---
layout: post
title:  Forager 모작 - 오늘한일
date:   2020-10-12T23:00:00+0900
author: Kijung Luke Kim
categories: [Project, Forager]
tags: [game, forager]
image: /assets/img/posts/forager.jpg
---

## 1. 몬스터 (에니미 클래스) 수정
---
 
- 상속 관계 재정립 (*완료!*)
    
    - 스폰매니저 : 일정시간마다 다양한 형식으로 몬스터의 종류와 수가 스폰되는 알고리즘의 코드의 집합.
    - 유닛매니저 : 업데이트, 렌더, 추가, 삭제, 길찾기 알고리즘의 결과값을 푸시
    - 에너미 : 자신의 현재 타일 좌표와 이동경로 타일 인덱스를 가짐
    - 스컬 : A* 알고리즘 결과를 받아서 최적의 경로로 이동

- A* 길찾기 알고리즘 수정 (*완료!*)

    - 포리저 타일맵 클래스에 맞춰 코드 변경.

```cpp
vector<int> Astar::pathFinding(vector<tile> vTile, int startidx, int endidx, bool checkwall, bool checkdiagonal)
{
	this->init(vTile);
	_startNode = _totalNode[startidx/MAPTILEX][startidx % MAPTILEX];
	_endNode = _totalNode[endidx /MAPTILEX][endidx % MAPTILEX];

	//길찾기 시작
	//검색시 우선 오픈리스트에 담는다
	//F와 H값 가장 작은 값을 지닌 노드를 현재노드로 변경한다
	//기존노드는 오픈리스트에서 삭제 후 클로즈리스트로 이동
	//길을 다 찾았다면 클로즈리스트를 거꾸로 정렬한 값을 파이널 리스트에 저장

	//1. 시작노드가 있어야 출발이 가능하니
	//시작노드를 오픈리스트에 추가를 해줘야 한다
	_openList.push_back(_startNode);

	//2. 오픈리스트안에 담겨 있는 벡터를 검사해서
	//종료노드에 도착할때까지 무한 루프
	while (_openList.size() > 0)
	{
		_curNode = _openList[0];

		//오픈리스트중 F가 가장 작거나 F가 같다면
		//H가 작은 걸 현재노드로 하고
		//현재노드를 오픈리스트에서 클로즈 리스트로 옮기기
		//비교를 하려고 하면 최소 시작노드에서 주변을 탐색한 이후
		//길찾기가 시작된다

		for (int i = 1; i < _openList.size(); i++)
		{
			if (_openList[i]->F <= _curNode->F && _openList[i]->H < _curNode->H)
			{
				_curNode = _openList[i];
			}
		}

		//클로즈 리스트에 넣어둔다
		for (int i = 0; i < _openList.size(); i++)
		{
			if (_curNode == _openList[i])
			{
				this->delOpenList(i);
				_closeList.push_back(_curNode);
			}
		}

		//현재노드가 마지막 노드와 같냐? (길찾았다)
		if (_curNode == _endNode)
		{
			node* endNode = _endNode;
			vector<node*> tempNode;
			//마지막 노드로부터 시작노드까지 부모노드를 벡터에 담는다
			while (endNode != _startNode)
			{
				tempNode.push_back(endNode);
				endNode = endNode->parentNode;
			}

			for (int i = tempNode.size() - 1; i > 0; i--)
			{
				int tileIndex = tempNode[i]->idy*MAPTILEX + tempNode[i]->idx;
				_finalList.push_back(tileIndex);
			}

			_isFind = true;
			//종료하고 빠져 나온다
			return _finalList;
		}

		//상하좌우
		addOpenList(_curNode->idx, _curNode->idy - 1);	//상
		addOpenList(_curNode->idx, _curNode->idy + 1);	//하
		addOpenList(_curNode->idx - 1, _curNode->idy);	//좌
		addOpenList(_curNode->idx + 1, _curNode->idy);	//우


        //대각선으로도 길을 찾고싶다면?
		if (checkdiagonal) {
			//우상, 좌상, 우하, 좌하
			addOpenList(_curNode->idx + 1, _curNode->idy - 1);	//우상
			addOpenList(_curNode->idx - 1, _curNode->idy - 1);	//좌상
			addOpenList(_curNode->idx + 1, _curNode->idy + 1);	//우하
			addOpenList(_curNode->idx - 1, _curNode->idy + 1);	//좌하
		}
	}
}
```

## 2. 발표 준비
---

> 깃 브랜치 머지 후 정리. (*완료!*)
