기능별 단위 테스트
=============

코드 기반의 단위 테스트말고 UI에서 기능(복잡한 기능)단위로 단위 테스트를 수행하고 싶은 경우

## 6.1 개발자가 확인할 단위 기능 테스트

기능 단위의 테스트 = 블랙박스 테스트

### 정렬 기능의 단위 테스트

정렬 기능을 생각한다고하면 하나하나 정렬하는 걸 생각해야할텐데
기능 단위의 단위 테스트 방법의 기본 요소를 고려해야함
- 단위 기능 경곗값
- 조합

**단위 기능 경곗값**
나이를 기준으로할 때
- 0세일때 프로그램이 에러 없이 처리할 수 있는가
- 그 경계에 있는 -1를 에러로 처리할 수 있는가
- 그리고 상한의 값은 몇인가
- 만약 나이에 알파벳이 포함되어 있다면 어떻게 될지?

또 다른 경곗값의 예로는
- 데이터의 건수가 0일때
- 데이터의 건수가 1일때
- 데이터의 건수가 매우 많을때

**조합**
일반적으로 조합할 때는 반드시 해당 조합에서 버그가 발생하기 쉬운가를 생각해야함 -> 데이터의 건수가 1인 경우를 확인했다면 2개의 요소를 조합해 기능이 제대로 동작하는지?

예를 들어 같은 나이일때는 그다음 기준인 입사 연도순으로 정렬, 입사 연도가 같을 때에는 순위대로 등 -> 먼저 데이터가 1과 2일때 확실하게 커버하고 n이라는 테스트 케이스를 적절한 개수로 한정해 작성할 수 있어야함

**단위 기능이 복잡한 경우는 자동화 테스트를 권장한다!**