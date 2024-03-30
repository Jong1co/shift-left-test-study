개발자 테스트의 기본 중 기본
=============

### **적어도 클래스 다이어그램과 시퀀스 다이어그램만은 작성하라!** 
->  왜냐?클래스 다이어그램이 있으면 큰 클래스를 방지할 수 있고 리팩터링의 효과도 시각화 할 수 있음

## 3.1 개발자가 반드시 알아야 할 테스트 기법

### 소프트웨어 개발 시 수행하는 테스트 목록

- 단위 테스트
- 조합 테스트
- 경곗값 테스트
- 상태 전이 테스트
- 탐색적 테스트
- 통합 테스트
- 시스템 테스트

모든 테스트를 수행할 수 없으므로
테스트 **라이프 사이클(단위 -> 통합 -> 시스템)** 의 각 단계에 맞춰 적절한 **테스트 방법(경곗값/조합/상태 전이)** 를 수행해야함

### 단위 테스트에서 이해해야할 3가지 기법

1. **경곗값 테스트 : 문자 그대로 경계를 테스트하는 방법**

    예를 들어
    어떤 시스템이나 애플리케이션이 나이를 입력 받아, 나이가 18세 이상 65세 이하인 경우만 "적합"으로 판단하는 기능을 가지고 있다고 할때  
    
    이 경우의 경계값은 18세와 65세. 그러므로 경계값 테스트에서는 이 경계값들 주변의 값을 사용하여 테스트 케이스를 만듬. 일반적으로 다음과 같은 값들을 테스트에 포함

    - 경계값 바로 아래의 값: 17세  
    - 경계값 자체: 18세, 65세  
    - 경계값 바로 위의 값: 66세

    이 경우 발생하는 버그 네가지

    - 올바른 코드
    ```
    if(a>=18 && b<=65){
        // 출력
    }else {
        // 에러 처리
    }
    ```

    - 닫힘 관계 버그 : >= 로 입력해야하는데 >라고 잘못 입력한 경우
    ```
    if(a>18 && b<65){
        // 출력
    }else {
        // 에러 처리
    }
    ```

    - 잘못 입력한 숫자, 요구사항 사양 오해 : 수 자체를 잘못 입력
    ```
    if(a>19 && b<64){
        // 출력
    }else {
        // 에러 처리
    }
    ```

    - 경계가 없음 : 조건문 작성하는 것을 잊은 경우
    ```
    if(a>=18 && b<=65){
        // 출력
    } // 이외의 예외를 처리하지 않음
    ```

    - 여분의 경계 : 불필요한 경계를 개발자가 작성함
    ```
    if(a>=18 && b<=65 && b>100){
        // 출력
    }else {
        // 에러 처리
    }
    ```
  
2. **상태 전이 테스트**

    '상태'를 모델화해서 테스트를 수행하는 방법. 크게 **상태**와 **전이**로 나뉨

    예시 (출처 : https://story.pxd.co.kr/1549)

    **애플리케이션 상태**  
    ![alt text](image-3.png)

    **상태 전이 매트릭스**  
    ![alt text](image-4.png)

    상태 전이 매트릭스에서 설계상 그런 이벤트가 발생하지 않을때 NA로 표시하는 것
    예를 들어 여기선 배송 중일때 반품을 할 수 없는데 반품할 수 있게된다면 버그인 셈

    상태 전이 테스트에서는 클래스나 함수 레벨에서 단위 테스트를 끝내고 해당 클래스가 인스턴스가 되어 다른 함수나 인스턴스가 호출되는지를 확인 = 시스템 전체에 대한 테스트 인 셈, 조기 단계의 테스트보다는 후반 테스트의 범주에 포함되는 경우가 많음

    개발자라면 상태 전이에 관한 에러 처리나 예외 처리를 고려해야함, 또한 어떤 상태에서 다음 상태로 전이할 수 없는지 어떤 파라미터가 필요한지 에러 메세지를 표시할지에 대해 테스트 담당자에게 전달해야함