## 목차  
- 동시성이 필요한 이유?
  - 미신과 오해
- 난관
- 동시성 방어 원칙
  - 단일 책임 원칙(Single Responsibility Principle, SRP)
  - 따름 정리(corollary): 자료 범위를 제한하라
  - 따름 정리: 자료 사본을 사용하라
  - 따름 정리: 스레드는 가능한 독립적으로 구현하라
- 라이브러리를 이해하라
  - 스레드 환경에 안전한 컬렉션
- 실행 모델을 이해하라
  - 생산자-소비자(Producer-Consumer)
  - 읽기-쓰기(Readers-Writers)
  - 식사하는 철학자들(Dining Philosophers)
- 동기화하는 메서드 사이에 존재하는 의존성을 이해하라
- 동기화하는 부분을 작게 만들어라
- 올바른 종료 코드는 구현하기 어렵다
- 스레드 코드 테스트하기
  - 말이 안 되는 실패는 잠정적인 스레드 문제로 취급하라
  - 다중 스레드를 고려하지 않은 순차 코드부터 제대로 돌게 만들자
  - 다중 스레드를 쓰는 코드 부분을 다양한 환경에 쉽게 끼워 넣을 수 있게 스레드 코드를 구현하라
  - 다중 스데르를 쓰는 코드 부분을 상황에 맞게 조율할 수 있게 작성하라
  - 프로세서 수보다 많은 스레드를 돌려보라
  - 다른 플랫폼에서 돌려보라
  - 코드에 보조 코드(instrument)를 넣어 돌려라. 강제로 실패를 일으키게 해보라
  - 직접 구현하기
  - 자동화
- 결론

## 아래 부분은 그냥 가져온 것으로 포맷만 참고해서 내용 수정할 것

## Intro
이전 챕터에서 코드, 코드 블록, 함수 구현 방법과 함수간의 관련 맺는 방식을 공부 했지만  
하지만 좀 더 차원 높은 단계까지 신경 쓰지 않으면 코드를 얻기는 어렵다.
이 장에서는 클래스를 다룬다.

## 클래스 체계
JAVA Convention에 따르면 가장 먼저 변수 목록이 나온다.
**static public --> static private --> private 인스턴스 --> (public은 필요한 경우가 거의 없다)**  
변수목록 다음에는 공개 함수가 나온다. 비공개 함수는 자신을 호출 하는 공개 함수 직후에 나온다.  
즉, 추상화 단계가 순차적으로 내려간다.
