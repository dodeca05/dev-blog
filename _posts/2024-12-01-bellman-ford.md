---
layout: single
title: 벨만 포드 알고리즘
categories: coding algorithm
---

벨만 포드알고리즘은 다익스트라 알고리즘과 함께 그래프에서 최단 경로를 구할대 많이 이용되는 알고리즘 입니다.

다익스트라와 차이점이 있다면 기본적으로 다익스트라 보다 오래 걸리지만 가중 그래프에서 엣지가 음수일때 음수 루프를 감지해낼 수 있습니다

벨만포드는 먼저 출발지에서 해당 노드까지 거리가 얼마인지 저장하는 테이블을 준비해두고 해당 테이블은 출발지를 0, 그외는 무한으로 초기화를 합니다.

그 다음은 이제 하나의 사이클을 돌 것인데요. 출발지로 부터 거리가 0이 아닌 노드들을 돌면서 인접한 노드들과 거리가 얼마인지 일일이 업데이트를 해주는 겁니다.

출발지가 s, 지금 살펴보고 있는 노드를 n, n의 인접노드를 m 이라고 할때 거리를 저장하는 테이블에 출발지로 부터 m의 거리를 s->n + n->m 의 값으로 업데이트를 해줍니다.

물론 테이블에 기존에 있는 값이 더 작으면 업데이트를 하지 않고 넘어갑니다.

이런식으로 모든 노드를 하나씩 살펴본 것이 하나의 사이클 입니다.

이 사이클을 노드개수 - 1번 반복하거나 하나의 사이클에서 업데이트가 발생하지 않을 떄 까지 반복합니다.

이를 그림으로 표현하면 다음과 같습니다.

처음에 그래프가 다음과 같이 있다고 가정해봅니다.

![KakaoTalk_Photo_2025-01-02-00-14-38](https://github.com/user-attachments/assets/53797b99-e8be-4430-ae7c-6c6c1b46c1bb)

노드를 1, 2, 3.. 이렇게 순서대로 방문하면서 위의 사이클을 실행합니다.

그러면 다음과 같이 최단거리가 구해집니다.

![KakaoTalk_Photo_2025-01-02-00-17-45](https://github.com/user-attachments/assets/56f16ab8-64f7-41da-9a35-9950a9bb96e1)

파란색은 첫번째 사이클에서 결정된 거리고 노란색은 두번째 사이클에 결정된 거리입니다.

위의 그래프는 두번의 사이클만에 모든 최단 거리가 구해졌습니다.


만약 노드개수 번째로 사이클을 돌렸을때 여전히 업데이트가 발생한다면 그 그래프는 음수 루프가 있다는 겁니다. 위의 그래프에서 6->5 거리를 -1로 만들어 음수 루프를 만들고 나서 업데이트가 발생되지 않을때 까지 사이클을 반복하면 다음과 같이 됩니다.

![KakaoTalk_Photo_2025-01-02-00-20-42](https://github.com/user-attachments/assets/9cb2144c-0598-4379-bc08-84dce42b426e)

