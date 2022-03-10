# 1. 객체
## 1) 클래스
1. 접근 제어자 : 외부에서의 접근 속성
  - `public` : class파일에서 단 한 개만 존재 가능함. ( _public class이름 == class 파일 이름_ )
  - `privte` : 
  - `protected` : 

2. 멤버 변수(member varication) _= 객체의 속성_
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





# 2.