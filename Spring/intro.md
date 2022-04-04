# Web 개발이란?
## 1. Web의 종류
- `Web Site` : Naver, Google 등
- `API` : Kakao Open API, Google Open API 등
- `User Interface` : Chrome, Explorer, Smart Watch, IP TV 등

## 2. Web 기본 3가지 요소
- `URI` _(Uniform Resource Identifier, 리소스 식별자)_ : 다양한 정보에 접근할 수 있는 정보
- `HTTP` (_Hyper text Transfer Protocol, 어플리케이션 컨트롤)_ : 주고 받을 때 사용하는 프로토콜
- `HTML` _(Hyper Text Markup Language, 하이퍼미디어 포멧)_ : 주고 받는 정보

## 3. REST API
: Representational State Transfer (자원의 상태 전달)를 의미하는 네트워크 아키텍처
1. `Clint, Server` : 클라이언트와 서버가 서로 분리 독립적이어야함
2. `Stateless` : 클라이언트의 상태를 서버에 저장하지 않는다.
3. `Cache` : 클라이언트는 서버의 응답을 Cache 할 수 있어야 한다. (서버 부하 저감 목적)
4. `Layered System` _(계층화)_ : 방화벽, 게이트웨이, 프록시 등 다양한 계층 형태로 구성이 가능해야하고 확장할 수 있어야함
5. `인터페이스 일관성` : 이키텍처를 단순화시켜 작든 단위로 분리하여, 클라이언트 및 서버가 독립적으로 개선될 수 있어야함
6. `Code on Demand` : 자바 애플릿, 자바스크립트, 플래시 등 특정한 기능을 서버로부터 클라이언트가 전달받아 코드를 실행할 수 있어야함

### 1) REST 적정성 판단 기준 (인터페이스 일관성 준수 여부)
1) 자원의 식별 (URI의 사용)
    - http://foo.co.kr/user/100
        - 리소스 : user 
        - 식별자 : 100
2) 메시지를 통한 리소스 조작 
    - 데이터 전체를 전달하는 게 아닌, 메시지 형태로 전달해야됨
3) 자기 서술적 메시지
    - 요청하는 데이터가 어떻게 처리되어져야 하는지 충분한 데이터를 포함할 수 있어야 한다.
4) 애플리케이션 상태에 대한 엔진으로써 하이퍼미디어
    - 응답만 하는것이 아닌 서버에 관련된 링크 정보도 함께 전달되어야함

## 4. URI 설계 패턴 
1. URI : 특정 자원을 나타내는 주소 (유일한 값)
2. URL : 특정 파일의 위치를 식별하는 주소 _(URI가 더 큰 개념)_

### `★ URI 설계 원칙`
1. 슬래시(/)는 계층 관계를 나타내는데 사용한다.
2. URI 마지막 슬래시(/)는 포함하지 않는다.
3. 하이픈(-)은 URI가독성을 높이기 위해 사용할 수 있다. __`(밑줄 X)`__
4. URI 경로는 소문자를 사용한다.
5. 파일 확장자는 URI를 포함하지 않는다.
6. 프로그래밍 코드, 오픈소스, 프레임워크 등을 나타내는 단어는 URI에 사용하지 않는다.
7. 세션 ID를 포함하지 않는다.
8. Method를 표현하지 않는다.
9. 명사 단어는 복수형을 사용한다.
10. 컨트롤러 이름으로는 동사를 사용한다.
11. 경로가 변경되는 부분 유일한 값으로 대체한다.
12. CRUD 기능(Create, Read, Update, Del)을 나타내는 단어를 URI에 사용하지 않는다.
14. URI 쿼리는 검색조건을 표현할 떄 사용한다. _(.../web-master?chapter-2&page=0)_
15. API, 개발타 포탈에 있어 서브 도메인은 일관성 있게 만들어야한다. _(fastcampus.co.kr -> api.fastcampus.co.kr)_

## 5. HTTP 프로토콜
- Request <-> Response 형태의 통신 방법
- HTTP 요청 메소드 8가지

    |요청|의미|CRUD|
    |-|-|-|
    |GET|읽기|Read|
    |POST|생성/추가|Create|
    |PUT|생성/갱싱|Create/Update|
    |DELETE|삭제|Delete|
    |HEAD|헤더 읽기||
    |OPTIONS|메소드 읽기||
    |TRACE|요청메시지 반환||
    |CONNECT|프록시 동작의 터널 접속으로 변경||
- HTTP 응답

    |응답|의미|
    |-|-|
    |1XX|처리중|
    |2XX|성공| 
    |3XX|리다이렉트|
    |4XX|클라이언트 에러| 
    |5XX|서버 에러|

# Spring 개요
- 20여가지의 [프레임워크](https://spring.io/projects/spring-framework) 제공
    - 예) 스프링부트, 스프링데이터, 스프링배치, 스프링시큐리티, 스프링클라우드
- 스프링의 주요 특징
    - 의존관계주입(IoC/DI)
    - 관점중심프로그램(AOP)
    - 이식가능한추상화(PSA)

## 1. IoC (Inversion of Control, 제어 역전)
- new 생성자가 아닌 `Spring Container`에 맡긴다.
- 즉, 개발자가 관리하는 것이 아닌 `프레임워크가 객체를 관리`한다는 의미

## 2. DI (Dependency Injection)
- 의존성에서 벗어나있어, 코드 테스트하기 용이하다. 
- Mock을 통해 코드 테스트가 가능하다.
- 코드 확장/변경이 용이하다.
- 순환 참조를 막을 수 있다.

## 3. AOP (Aspect Oriented Programming, 관점 지향 프로그램)
- Web Layer : REST API 제공 
- Business Layer : 주요 로직
- Data Layer : 데이터베이스 연동
