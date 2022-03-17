# 1. Object Class
## 1) 기본 사항
- `root class`로 모든 클래스들의 최상위 클래스
- java.lang이라는 패키지에 포함되어 있으며, 별도 호출 없이도 사용 및 상속된다.
- `Object`의 메서드 일부는 재선언하여 사용할 수 있다.
## 2) 주요 메서드
### (1) toString()
- 기본 출력 메서드 (기본 : 참조 주소 출력)

```java
//toString 재선언을 통해 Class 멤버변수의 값 출력
class Book{
	public Book(String title, String author) {
		this.title = title;
		this.author = author;
	}
	
	public String toString() {
		return title + "," + author;
	}
}
``` 
## (2) equals() / hashCode()
- equals : 기본 비교 메서드 (기본 : 참조 주소 비교)
- hashCode : 참조주소 출력 메서드
```java
// equals을 주소가 아닌 특정 값으로 비교
@Override
public boolean equals(Object obj) {
    if(obj instanceof Student) {
        Student std = (Student)obj;
        if(this.studentId == std.studentId )
            return true;
        else return false;
    }
    return false;
}

// hashCode를 참조주소가 아닌 특정 값으로 출력
@Override
public int hashCode() {
    return studentId;
}

// 출력 부분
Integer i1 = new Integer(100);
Integer i2 = new Integer(100);

System.out.println(i1.equals(i2));
System.out.println(i1.hashCode());
System.out.println(i2.hashCode());
```

## (3) clone()
- 클래스를 있는 그대로 복제
- `clonable`이라는 클래스(?)를 `상속`한 경우에만 적용 가능하다.
- 따로 지정할 것 없이 리턴값만 작성되면 된다.
```java
public class Student implements Cloneable{
    ...
	@Override
	protected Object clone() throws CloneNotSupportedException {
		return super.clone();
	}
}
```

## (4) String
- String : `final`로 선언되어 있어 내용 변경 시 불필요한 데이터가 계속 축적됨. (비효율)

## (5) StringBuilder(), StringBuffer()
- StringBuilder() : 단일 쓰레드에서 사용
- StringBuffer() : 멀티 쓰레드에서 사용
```java
// 생성자로 선언해야함
StringBuilder res1 = new StringBuilder("나의 ");
StringBuilder res2 = new StringBuilder("이름은?");

// + 연산자를 사용할 수 없고, append를 사용하여 문자 연결해야됨.
// (res1 값이 변경되는 메서드임을 꼭 참고하자)
System.out.println(res1.append(res2));
```

## (6) textBlock (""" """)
- JDK 13 이후에 도입되었으며, java/ json 파일과 연결성이 좋음
```java
String res3 = """
        나의 살던 고향은
        꽃 피던 사안 꼬올
        """;

String res4 = """
        응 촌놈~
        """;

System.out.println(res3 + res4);
```

# 2. Class Class
## 1) 기본
- 클래스에 대한 전반적인 분석기능을 제공하는 클래스
- 만들어진 클래스를 `동적 로드`하기 위해, _Class.forName("클래스")_ 가 자주 사용됨.
```java
Class c = Class.forName("myClass");
```
### (1) 동적 로딩
- 어떤 값/ 데이터 타입인지 모르다가, 추후 정해진 것으로 실행되는 기능
- 정해진 시점에 값/ 데이터를 호출하지 못하게되면, 심각한 오류가 발생할 수 있다.

### (2) 리플렉션 프로그래밍 (reflection programming)
- Class 클래스를 사용하여, 생성자/멤버변수/메서드를 확인할 수 있고, 인스턴스를 만들어 메서드를 호출하는 방식
- 현재 메모리(쓰레드)에 객체가 없는 경우, 원격 프로그래밍, 객체의 타입을 알 수 없는 경우에 사용
- 일반적인 경우에는 사용되지 않음
```java
// 외부의 모듈을 사용하는 경우, 내부 메서드들을 확인하고 싶을때 활용
Class c = Class.forName("java.lang.String");

constructor[] cons = c.getConstructors();
for (constructor co : cons) {
    System.out.println(co);
}
```
```java
// 사용하려는 모듈이 외부에 있는 경우에 사용됨

// 1. 외부에 있는 모듈 호출
Class c1 = Class.forName("ch04.Person");
Person person1 = (Person)c1.newInstance();

// 2. 사용하고자하는 클래스 선택
Class[] parameterTypes = {String.class};
Constructor cons = c1.getConstructor(parameterTypes);

// 3. 사용하고자하는 클래스의 인수 선택
Object[] initargs = {"김유신"};
Person personLee = (Person)cons.newInstance(initargs);
System.out.println(personLee);

}
```