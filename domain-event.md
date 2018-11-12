# 도메인 이벤트

## 왜 필요한가?

## 단계적 도입

Level 0: No events at all
    - 모든걸 setter / getter로 처리
    - 도메인 논리라고 할 게 없는 상태
    - Rest API를 가장 쉽게 구현하는 방법이자 잘못된 방법

Level 1: Explicit operations
    - 2회 이상의 setter를 한 번에 호출하는 경우 메소드 등으로 리팩토링

Level 2: Some operations as events
    - 일부 중요한 operation을 이벤트로 처리
        예: 객체의 생성 등
    - Domain events as state transitions
    - Expose important events to interested parties via feeds

Level 3: Event Sourcing
    - Only storing events that happened to the system
    - Create read model