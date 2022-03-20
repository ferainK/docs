# 객체지향

## 1. 객체의 3가지 요소
1. 상태 유지 (객체의 상태) : 상태정보를 저장/유지하기 위한 멤버변수(`Variable`) 필요
2. 기능 제공 (객체의 책임) : 특정 기능을 제공하기 위한 `Method` 제공 필요 (상태정보를 변경도 Method를 통해 수행)
3. 고유 식별자 제공 (객체의 유일성) : 각 객체는 고유한 식별자를 가져야 한다. (`Primary Key`)

## 2. 물리객체 vs 개념객체
1. 물리 객체 : 실제 사물이 존재함 _(Ex. 급여 관리 시스템 - 직원 정보, 통장 정보 등)_
2. 개념 객체 : 서비스 제공을 위한 business logic을 처리하는 부분 (ATM 시스템 - 입금/출금 처리)

## 3. 객체지향 4가지 특성
1. 캡슐화 (추상화 제공, 재사용성 향상, 유지보수 향상)
    - 객체의 속성(`Variable`)을 보호하기 위해 사용 _(필요시, private로 선언)_
    - 객체의 기능(`Method`)은 객체 속성(`Variable`)의 무결성을 위해, 유효성 검사 로직 (`Validation`) 설계가 필요하다.
    - 객체의 속성을 변경하기 위한 Method 설계 필요  _(Getter/Setter)_
    - 각 Method는 서로 연계되도록 Method 설계 필요 _(Ex. 속성 추가/삭제)_
    - 기본적인 데이터 치리를 위한 기본 Method 설계 필요 _(Create/Read/Update/Delete)_
    - 객체의 생명주기 처리를 위한 Method 설계 필요 _(destroy/ disconnect/quit 등)_
    - 다른 객체를 직접 불러오지 않고, 필요한 속성만 가져와 사용함
2. 상속 (확장성 향상, 로직 이해도 향상, 재사용성 향상, 유지보수 향상)
    - 하위로 내겨갈수록 구체화
3. 다형성 (확장성 향상, 유지보수 향상)
    - 오버라이딩
    - 최상위 객체로 인스턴스화하고 상속받은 객체로 생성자를 만들 수 있다.
        ```java
        Unit 저글링 = new 저글링();
        Unit 히드라 = new 히드라();
        Unit 뮤탈 = new 뮤탈();
        
        // Unit에 대한 Method만 만들면 된다!!
        Private void unitMove(Unit unit){
            unit.move()
        }
        ```
4. 추상화
    - 객체의 공통적인 부분을 분리하여 재조합하는 부분

## 4. 객체지향 설계 5대 원칙
- 응집도와 결합도 : `응집도`는 `높고`, `결합도`는 `낮은`게 유리
    - 응집도 : 모듈 내 기능 독립성
    - 결합도 : 모듈간 상호의존성

1. 단일 책임 원칙 (SRP, Single Responsibility Principle)
    - 유지보수 및 재사용성을 높이기 위해, 공통 기능에 대해 Method 분리/재조합
    - _최상위 클래스/인터페이스에 기능(`Method`)을 부여하고 오버라이딩하는 형태로 사용됨_
2. 개발 폐쇄 원칙 (OCP, Open Closed Principle)
    - 자신의 확장에는 열려있고, 주변 변화에는 닫혀 있어야 한다.
    - _상위 클래스/인터페이스를 중간에 두어 사용됨_
    ![참고사진](../rcs/%EC%8A%A4%ED%81%AC%EB%A6%B0%EC%83%B7%202022-03-20%20%EC%98%A4%ED%9B%84%203.27.17.png)
3. 리스코프 치환 원칙 (LSP, Liskov Substitution Principle)
    - 상위/하위 클래스/인터페이스의 관계가 명확해야 함
4. 인터페이스 분리 원칙 (ISP, Interface Segregation Principle)
    - 클라이언트는 자신이 사용하지 않는 메서드에 의존관계를 맺으면 안된다.
    - OCP, SRP 원칙에 따라 인터페이스를 분리하여야함
5. 의존 역전 원칙 (DIP, Dependency Inversion Principle)
    - 변하기 쉬운 것에 의존하지 말아야 한다.

## 5. POJO JAVA (Plain Old Java Object)
- 순수한 자바 오브젝트
### 1) POJO의 특징
1. 특정 규약에 종속되지 않는다
    - 외부 _(특정 Library, Module)_ 에 의존하지 않는다.
2. 특정 환경에 종속되지 않는다.
    - 특정비즈니스 처리 로직을 처리하는 부분의 http request, sesstion 등, @Annotation도 의존성을 가진다고 볼 수 있다.

### 2) POJO Framework
1. __Spring / Hibernate__
    - 개발자는 POJO에 벗어나, 서비스 로직에만 집중할 수 있도록 지원 
