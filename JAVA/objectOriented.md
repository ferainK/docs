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
2.  힙 메모리 (`=동적 메모리`)<br> : 필요할 때 메모리에 할당하고, 사용하지 않으면 자동으로 메모리에서 삭제됨 (인스턴스로 선언된 클래스의 멤버변수 등) <br><br>
3. 데이터 영역 <br> : 처음 프로그램이 실행되어 메모리에 할당되는 영역

<br>
<br>

# 2. 클래스의 속성
## 1) 접근 제어자
### (1) 접근 제어자의 종류
  - __생략__ : `package 내부`에서만 접근 가능
  - __private__ : `Class 내부`에서만 접근 가능
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

## 2) this : 멤버변수의 명시적 표현
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
## 3) static : 인스턴스에서 분리화
  1. 동일한 Class의 `여러 인스턴스`에서 `공통`으로 사용되는 변수
  2. `인스턴스` 생성할 필요 없이 사용 가능하다.
  3. 처음 로직이 구동되면서, `데이터 영역`에 메모리 할당
  4. Class의 `static 메서드`에서는 `멤버변수 사용 불가`

<br><br>

### (1) 싱글톤 패턴
- 단 하나의 인스턴스만 생성학 싶을 때 
  ```java
  public class Company() {
    private static Company instance = new Company();
    public static Company getinstance() {
      if (instance == null){
        instance = new Company();
      } else{
        return instance;
      }
    }
  }
  ```

# 2. 배열
## 1) 일반 배열
- `초기화하지 않는 경우`, 데이터 타입에 따라 `0` 혹은 `" "`로 초기화되므로 주의하자!
```java
// 선언 후 초기화 방법 (1차 배열)
// #1
int[] arr = new int[3];
arr = {10, 20, 30};

// #2
int[] arr;
arr = new int[] {10, 20, 30};
```

```java
// 동시 선언/초기화 방법 (2차 배열)
// #1
int[][] arr = new int[][] {{10, 20, 30}, {3,4,5}, {100, 200, 300}};

// #2
int[][] arr = {{10, 20, 30}, {3,4,5}, {100, 200, 300}};
```
## 2) 객체 배열
- `초기화하지 않는 경우`, `null`로 초기화되므로 주의하자.
- 객체는 참조변수로 배열 안에는 주소값(4 or 8바이트)이 저장된다.
### (1) ArrayList
- `java.util`에서 제공하는 Class
- 객체 배열의 경우, `ArrayList<'Class명'>`으로 선언하는 것이 일반적
- 주요 메서드 (E : 문자형)

  |반환값|메서드|설명|
  |--|--|--|
  |int|`size()`|전체 요수의 수 반환|
  |boolean|`isEmpty()`|배열이 비어있는지 확인|
  |boolean|`add(E 'value')`|배열 값 추가 <br> (객체 배열의 경우, 생성자 지정 필요)|
  |E|`get(int 'index')`|index 위치의 요소 반환|
  |E|`remove(int 'index')`|index 위치의 요소 삭제|

```java
import java.util.ArrayList;
import 'class 위치';

public class test{
  ArrayList<'class이름'> arr = new ArrayLIst<>();
  arr.add(new Book("책1", "저자1")) 
}
```

### (2) 복사 종류
1.  얕은 복사
    ```java
    Book[] originArray = new Book[5];
    Book[] newArray = new Book[5];

    originArray[0] = new Book("책1", "저자1");
    originArray[1] = new Book("책2", "저자2");
    originArray[2] = new Book("책3", "저자3");
    originArray[3] = new Book("책4", "저자4");
    originArray[4] = new Book("책5", "저자5");

    System.arrayCopy(originArray, 0, newArray, 0, 5)
    // 배열이름, 배열 시작 인덱스, 새로운 배열 이름, 새로운 배열 시작 인덱스, 복사할 배열 수
    ```

2. 깊은 복사
    ```java
    Book[] originArray = new Book[5];
    Book[] newArray = new Book[5];

    originArray[0] = new Book("책1", "저자1");
    originArray[1] = new Book("책2", "저자2");
    originArray[2] = new Book("책3", "저자3");
    originArray[3] = new Book("책4", "저자4");
    originArray[4] = new Book("책5", "저자5");

    newArray[0] = new Book();
    newArray[1] = new Book();
    newArray[2] = new Book();
    newArray[3] = new Book();
    newArray[4] = new Book();

    //배열의 모든 값을 직접 초기화해줘야함....
    for (int i = 0; i < originArray.length; i++){
      newArray[i].setTitle(originArray[i].getTitle());
      newArray[i].setAuthor(originArray[i].getAuthor());
    }
    ```