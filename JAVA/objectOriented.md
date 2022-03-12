# 1. 클래스 구성요소
- 클래스에는 `멤버 변수`, `생성자`, `메서드`가 있다.
- 메스드나 생성자는 비슷해 보이지만, `생성자`는 `클래스 이름과 동일한 메서드`이다.


<br>

## 1) 멤버 변수
- `멤버 변수`는 객체의 속성이다.
- 클래스 내부에서만 사용되는 변수이다.
    ```java
    public class Student{
      //멤버 변수
      int studentNumber;
      String studentName;
      int majorCode;
      String majorNmame;
      int grade;
    }
    ```

<br>

## 2) 메서드 
- 메서드(`method` = `member function`)는 클래스에 종속된 함수
- 메서드에는 반환값(`return`)이 있다.
    ```java
    public class Student{
      //멤버 변수
      int studentNumber;
      String studentName;
      int majorCode;
      String majorNmame;
      int grade;

      //메서드
      public void showUserInfo() {
        System.out.println(userId + " 아이디의 이름은 " + userName + "입니다.");
      }

      public String getUserName() {
        return userName;
      }

      public void setUserName(String name){
        userName = name;
      }
    }
    ```

    > ※ _함수 (`function`) : 클래스와 무관한 단독 객체_
    >    ```java
    >    //반환이 있는 경우
    >    int add(int num1, int num2){
    >      int result;
    >      result = num1 + num2;
    >      return result;
    >    }
    >
    >    //반환이 없는 경우
    >    void infoming(String msg){
    >      if (msg="실패"){
    >        System.out.println("실패하였습니다.")
    >      }
    >    }
    >    ```

<br>

## 3) 생성자 

- 생성자는 `클라이언트 모듈`에서 `호출`할 때 사용된다.
- 서비스 모듈에서 `class`를 생성할 때, 적어도 `하나 이상의 생성자`가 있어야 함.
- 생성자는 반환값이 없고, 메서드만 반환값이 있다.

### (1) 인스턴스
-  클라이언트 모듈에서 클래스를 `독립된` 변수 형태로 `호출`하는 것
    ```java
    //user1과 user2는 서로 연관성이 없음
    UserInfo user1 = new UserInfo();
    UserInfo user2 = new UserInfo();
    ```
    > _※ `인스턴스 생성`과 `변수 선언`과의 차이점_
    >
    > ```java
    >// 인스턴스 생성 : 생성자 호출 
    >//                (힙 메모리 할당하는 과정)
    >User user1 = new User();
    >
    >// 선언 (스택 메모리에 할당하는 과정)
    >int userName = "이철우";
    >```

### (2) 기본 생성자 (defalut constructor)
- 서비스 모듈에서 class에 별도 생성자를 만들지 않는다면 `기본 생성자`가 만들어진다.

### (3) 오버로딩 (overloading)
- 서비스 모듈에서 클래스를 호출할 때 다양한 형태의 생성자 제공 위해, `매개변수를 달리한 여러 생성자` 생성된다. 

<br>

## 4) (참고) 메모리 할당
1.  스택 메모리<br> : 함수가 호출되면 스택 메모리에 지역변수가 쌓이고, 함수가 종료되면 스택 메모리에서 삭제됨 (함수/메서드 등) <br><br>
2.  힙 메모리 (`=동적 메모리`)<br> : 필요할 때 메모리에 할당하고, 사용하지 않으면 자동으로 메모리에서 삭제됨 (인스턴스로 선언된 클래스의 멤버변수 등)
<br>
<br>

# 2. 클래스의 속성
## 1) 접근 제어자
### (1) 접근 제어자의 종류
  - __생략__ : `package 내부`에서만 접근 가능
  - __privte__ : `Class 내부`에서만 접근 가능
  - __protected__ : `package 내부` 및 `상속한 Class`에서만 접근 가능
  - __public__ : `어디에서든` 접근 가능

### (2) get() / set() 메서드
  - private에도 접근할 수 있게 만든 public 메서드
    ```java
    // private 멤버변수 선언
    private int result = 10;

    // get 메서드
    public int getResult() {
      return this.result;
    }
    // set 메서드
    public void setResult(int result){
      this.result = result;
    } 
    ```

### (3) 정보은닉 및 캡슐화
  - 멤버변수(boolean)와 if문을 통해, ① 입력값이 옳바른지 확인할 수 있고, 이를 통해 ② 데이터 오염을 방지할 수 있다.
  - `꼭 직접 구현해보세용^^`

## 2) this
  1.  인스턴스 자신의 메모리에 할당된 주소<br> : 인스턴스 저장되어 있는 멤버변수/인스턴스를 호출할 때 사용

      ```java
      //멤버변수
      static int data = 30;

      //메서드
      public setData(int data){
        this.data = data;  //focus
      }
      ```

      2. 클래스 내부에서 생성자가 오버로드 되어있는 다른 생성자를 호출할때 사용
      ```java
      //생성자1
      public MyClass() {
        this("이름 없음", 1);  //focus
      }

      //생성자2
      public MyClass(String name, int age) {
        this.name = name;
        this.age = age
      }
      ```
# 2.