코드 리뷰
=============

## 8.1 코드 리뷰란

코드 리뷰란 다른 사람이 작성한 코드를 지적하는 것이 아니라 본인이 깨닫는 것에 중점을 둘 것! 
지적보다는 여기는 왜 이렇게 작성되어 있나요?라고 질문하는 형식을 갖춤으로써 본인이 학습하는 것

사실 리뷰가 테스트보다 더 효율적인 버그 발견 방법 -> 효율적으로 운영하려면 코드 리뷰 전에 기계가 검출할 수 있는 버그는 걸러내고, 사람은 정말 최소한의 작업만 하는 구조로 만드는 것

일반적으론
- 풀리퀘스트 -> 리뷰 -> 병합을 하는데
- 풀리퀘스트 -> 단위테스트실행 -> 실행결과를(코드와 함께) 리뷰 -> 병합

단위 테스트가 실패하는 상태에서 리뷰를 진행해도 의미가 없으니 실행하고 리뷰해!

## 8.2 페어 프로그래밍

페어 프로그래밍을하면 서로 피드백도 해주고 좋은거 알겠어 그런데 사이가 안좋은 동료와 페어프로그래밍은 끔찍할 것 같은데..

그렇다면 다음 조건을 써보세욤~

- 코딩 규약이 있으므로 불필요한 논의가 사라짐
- 모든 사람이 재충전도히어 있고 휴식 시간이 충분하므로 뷸필요한 논의X
- 페어로 함께 테스트를 작성하고 구현에 들어가기 전에 서로 이해한 내용을 조율할 기회
- 페어는 네이밍이나 기본 설계를 결정하는 메타포를 가짐
- 페어는 단순한 설계 수행, 현재의 진행 상황을 이해

그런데 시간이 없잖아요 그러면..

개발자 레벨이 낮다면 페어프로그래밍을 해보고, 높다면 페어 프로그래밍 하지말것. 중급이라면 간단한건 혼자서, 어려운건 함께
