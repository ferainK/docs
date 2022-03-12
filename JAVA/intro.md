# 1. 설치하기
## 1) JAVA 설치 하기
- `[사용자용]` [JAVA JRE](https://www.oracle.com/java/technologies/downloads/#sjre8-windows) : 자바 실행 환경 (8버전까지만 무료 제공)
  - JDK 설치시, JRE는 자동으로 함께 설치된다. (버전업 하고 싶다면 별도 설치...)
- `[개발자용]` [JAVA JDK](https://www.oracle.com/java/technologies/downloads/#jdk17-windows) : 자바 개발 도구 (컴파일러 등 포함)
  - JAVA SE : JAVA stadard edition (일반 사용자) [무료, `상업용으로 사용 불가`]
  - JAVA EE : JAVA enterprise edition (기업용) [유료]
  - JAVA ME : JAVA micro edition (임베디드)

- `[IDE]` [Eclips](https://www.eclipse.org/downloads/)
  - 무료 사용 가능

- `[IDE]` [Intellij](https://www.jetbrains.com/ko-kr/idea/download/#section=windows)
  - community 버전만 무료 (JS 사용 불가, Spring 편의기능 미지원)

## 2) 구성하기
- `프로젝트(Project)` : 첫 문자는 `대문자`로 만들기 (_파스칼 케이스_)
- `패키지(package)` : 첫 문자는 `소문자`로 만들기 (_카멜 케이스_)
- `클래스(Class))` : 첫 문자는 `대문자`로 만들기 (_파스칼 케이스_)
- `변수/인스턴스(variable/instance)` : 첫 문자는 `소문자`로 만들기 (_카멜 케이스_)
  -  변수/인스턴스 이름은 __숫자, 영문,  `_` ,  `$`__ 만 가능

<br><br>

# 2. 자료형
## 1) 기본 자료형 
- __정수형__

  ||정수형|비고|
  |---|---|---|
  |1 Byte|byte|동영상, 음악파일, 실행파일|
  |2 Byte|shrot|잘사용하지는 않음<br>(C, C++ 호환시 사용)|
  |`4 Byte`|`int`|`기본 정수형`<br>(java에서 모든 숫자는 4byte로 되어 있음)|
  |8 Byte|long|숫자가 큰 경우<br>(숫자 뒤에 L을 붙여야함, ex) 12340000L )|


  - 진수 표현 방법
    ```java
    //10진수
    int num = 10;

    //2진수 (0b)
    int bNum = 0b1010;

    //8진수 (0)
    int oNum = 012;

    //16진수 (0x)
    int xNum = 0xA;
    ```

<br>

- __실수형__ ( _계산 시, 오차율 0.000001% 정도 발생하니 주의!_ )

  ||실수형|비고|
  |---|---|---|
  |`4 Byte`|`double`|`기본 실수형`|
  |8 Byte|float|자리수가 많은 경우<br>(숫자 뒤에 f을 붙여야함, ex) 0.1444f )|

<br>

- __문자형__ (_UNICODE 표준_, _UTF-16 인코딩_ )

  - 쌍따움표 (`"Hello"`) : `문자열 (string)`
  - 따움표 (`'A'`) : `문자형 (char)`
  

    ||문자형|비고|
    |---|---|---|
    |`2 Byte`|`char`|`기본 문자형`|

<br>


- __논리형__

  ||논리형|비고|
  |---|---|---|
  |`1 Byte`|`boolean`|`기본 논리형`|

<br>


- __와일드? 자료형__

||논리형|비고|
|---|---|---|
|<auto>|`var`|적절한 자료형으로 자동 변환<br>(한번 선언된 후 다른 자료형으로 변경 불가)|

## 2) 참조 자료형
1. String
2. Class

<br><br>

# 3. 선언 방식
## 1) 상수
```java
// 선언 및 초기화
final int PI = 3.14;

//선언 후 초기화
final int PI;
PI = 3.14;
```

## 2) 변수
```java
// 선언 및 초기화
var name = "부대찌개";
var price = 10000;

//선언 후 초기화
var name;
var price;

name = "부대찌개";
price = 10000;
```
> _※ 변수의 종류_
> 1. 지역변수 : 블럭( `{  }` ) 안에서만 사용되는 변수
> 2. 전역변수 : 클래스 전체에서 사용되는 변수
> 3. 매개변수 : 함수 외부에서 들어오는 변수
> 4. 인수?