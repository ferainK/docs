# 1. 상속
## 1) 기본
### (1) 접근 제어자의 종류
- __생략__ : `package 내부`에서만 접근 가능
- __private__ : `Class 내부`에서만 접근 가능
- __protected__ : `package 내부` 및 `상속한 Class`에서만 접근 가능
- __public__ : `어디에서든` 접근 가능

### (2) Usage
- Has-A 관계 (composition) : 일부 포함되는 관계
  - _(예)_ `Student` ↔ `Subject/Class/...`
- Is-A 관계 (is a relationship) :일반적인 개념과 구체적인 개념의 관계
  - _(예)_ `Employee` ↔ `Enginneer/Manger/...`

<br><br>

## 2) 기본 기능
### (1)  super
- 상위 클래스의 멤버변수/메서드를 호출하기 위함 (this와 유사?)
- 일반적으로는 상속 받은 상태라 super을 많이 사용하지는 않음
  ```java
  // 단일 상속만 가능함
  class B extends A {
    super.method1();
  }
  ```

### (2) Override
- 애노테이션인 `@Override`를 반드시 명시하여야만 함
- 애노테이션 : 컴파일러에게 특별한 정보 제공 (_@xxxx_)
- 행변환이 되지 않고 가상 메서드로 실행 주의! (`VIPUser에 오버라이드된 메서드로 실행됨`)
  ```java
  @Override
  public int priceUsedBonus(int price) {
    price *= (1 - this.saleRatio);
    return super.priceUsedBonus(price);
  }
  ```
## 3) 행변환
### (1) 업캐스팅 (upcasting)
- 행변환이되는 경우, 인스턴스 타입에 따라 멤버변수/메서드가 결정됨
- 메서드의 경우, 생성자의 오버라이드가 적용된다는점 주의! 
- ( ∵ 생성자에서 데이터 영역에 저장된 정보를 불러오고, 인스턴스의 각 변수에 주소를 할당 함)

    ```java
    User user1 = new VIPUser();
    // 단, user1은 User의 멤버변수/메서드만 사용 가능
    ```

- 다형성을 장점을 활용하기 위해 사용됨
    ```java
    // Silver 인스턴스를 VIP/Gold를 업캐스팅하여 명시적으로 코드를 나타낼 수 있음
    ArrayList<Silver> member = new ArrayList<>();
    member.add(new VIP("이철우"));
    member.add(new Gold("똥우지"));
    member.add(new Silver("우지챠"));

    member.get(0).showInfo();
    member.get(1).showInfo();
    member.get(2).showInfo();
    ```


### (2) 다운캐스팅 (downcasting)
- 업캐스팅한 인스턴스의 경우만, 다운캐스팅 가능함
  ```java
  // 일반적인 표현
  Silver member = new VIP()     // 업캐스팅
  if (member instanceof VIP) {
    VIP member = (VIP)member    // 업캐스팅 한 경우에만, 다운캐스팅 수행
  }
  ```

## 4) 프레임워크화 _(with 인터페이스)_
### (1) 추상 클래스 (abstract class)
- 추상 클래스는 인스턴스화할 수 없고, `상속만 가능`하다.
- 추상 클래스 내 `추상 메서드를 포함`할 수 있다.
- `추상 메서드`는 상위 클래스에서 `선언만` 되고, 상속 받은 클래스에서 구현(작성)해야만 한다.
  ```java
  //추상 클래스
  public abstract class Computer{
    public abstract void dispaly() //추상 메서드
    public void turnOn() {
      System.out.println("시작");
    }
  }
  ```
### (2) 템플릿 메서드 (template method)
1. 추상 메서드 (abstract method) : 선언만 하고, 상속 받은 클래스에서 구현(작성)
    ```java
    public abstract void dispay()
    ```
2. final 메서드 (final method) : 상속 받은 클래스에서 오버라이드 제한
    ```java
    final public void dispay(
      System.out.println("호호호");
    );
    ```

# 2. 인터페이스
## 1) 
- 일종의 설명서(specification)을 제공하기 위해 사용됨
- `추상 클래스 형태`로 작성되고, `모든 메서드` = `추상 메서드` / `모든 변수` = `상수`로 선언된다.
- 클래스 상속과 달리 여러 인터페이스를 implements할 수 있다.
  ```java
  public class Calculator implements interface{
    ...
  }
  ```