# 1. 클래스
## 1) 멤버 변수
- `멤버 변수`는 객체의 속성이다.
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
1. 접근 제어자 : 외부에서의 접근 속성
  - `public` : class파일에서 단 한 개만 존재 가능함. ( _public class이름 == class 파일 이름_ )
  - `privte` : 
  - `protected` : 



3. 메서드 (`method` = `member function`) : 클래스 모듈에 종속된 함수
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

4. 함수 (`function`) : 단독 모듈
    ```java
    //반환이 있는 경우
    int add(int num1, int num2){
      int result;
      result = num1 + num2;
      return result;
    }

    //반환이 없는 경우
    void infoming(String msg){
      if (msg="실패"){
        System.out.println("실패하였습니다.")
      }
    }
    ```

5. 인스턴스 : 클래스를 독립된 변수로 선언하는 것
    ```java
    //user1과 user2는 서로 연관성이 없음
    UserInfo user1 = new UserInfo();
    UserInfo user2 = new UserInfo();
    ```

## 2) 메모리
1.  스택 메모리<br> : 함수가 호출되면 스택 메모리에 지역변수가 쌓이고, 함수가 종료되면 스택 메모리에서 삭제됨 (함수/메서드 등) <br><br>
2.  힙 메모리 (`=동적 메모리`)<br> : 필요할 때 메모리에 할당하고, 사용하지 않으면 자동으로 메모리에서 삭제됨 (인스턴스로 선언된 클래스의 멤버변수 등)

## 3) 생성자 
- 클래스에는 `멤버 변수`, `생성자`, `메서드`가 있고, 메스드나 생성자는 비슷해 보이지만, 생성자는 클래스 이름과 동일한 메서드이다.
- 생성자는 서비스 모듈에서 호출할 때 사용된다.

```java
// 인스턴스 : 생성자 호출 (힙 메모리 할당하는 과정)
User user1 = new User();

// 선언 (스택 메모리에 할당하는 과정)
int userName = "이철우";
```

### (1) 기본 생성자 (defalut constructor)
- `class`에는 적어도 하나 이상의 생성자가 포함되어야함.
  - 별도 생성자를 만들지 않는다면 `기본 생성자`가 만들어짐
  - 기본 생성자 : 클래스와 이름이 동일한 메서드, 외부에서 호출되기 위해 사용됨
- 생성자는 반환값이 없고, 메서드만 반환값이 있다.

### (2) 오버로딩 (overloading)
- 서비스 모듈에서 클래스를 호출할 때 다양한 형태의 생성자 제공 위해, `매개변수를 달리한 여러 생성자` 생성 

<br>

# 2.