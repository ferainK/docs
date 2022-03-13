## 1. 연산자
1. 대입 연산자
    ```java
    a = 10
    ```

2. 산술/관계 연산자 (생략)
    ```java
    boolean bool1 = A && B
    boolean bool2 = A || B
    boolean bool2 = !A
    ```

3. 삼항 연산자 (조건 연산자) <br>
    : `조건식 ? 'true 결과' : 'false 결과'`
    ```java
    int A ? A : '값이 없습니다.'
    //결과 : 값이 없습니다.
    ```
4. 비트 연산자 (생략)

<br>

## 2. 조건문
### 1) if문

```java
Scanner scanner = new Scanner(System.in);
boolean bool = scanner.nextBool();

if (bool) {
    System.out.prinln(true);
} else if (!bool) {
    System.out.println(false);
}else {
    System.out.println('error');
}
```

### 2) switch-case문
- 예전 문법


    ```java
    int month, day;
    month = 3;

    switch(month) {
        case 1: case: 3 case 5: case 7: case 8: case 10: case 12:
            day = 31;
            break;
        case 4: case 6: case 9: case 11:
            day = 30;
            break;
        case 2: 
            day = 28;
            break;
        default:
            System.out.println('오류');
    };
    ```

- 최근 문법
    ```java
    int month = 3;
    int day = switch(month) {
        case 1, 3, 5, 7, 8, 10, 12 -> {
            yield 31;
        }
        case 4, 6, 9, 11 -> {
            yield 30;
        }
        case 2 -> {
            yield 29;
        }
        default ->{
            yield 0;
        }
    };

    System.out.println(day)
    ```
<br>

## 3. 반복묵
### 1) while문

```java
int num = 1;

while (num < 10) {
    num++;
}
//1, 2, 3, 4, 5, 6, 7, 8, 9, 10
```

### 2) do-while문

```java
int num = 0;

do{
    num++;
} while (num < 10);
//1, 2, 3, 4, 5, 6, 7, 8, 9, 10
```

### 3) for문

```java
for(int num = 1; num <= 5; num++){
    System.out.println(num);
}
```
```java
//참고) 무한 반복
for (;;){
    ...
}
```
```java
// foreach
for (int num : array){
    ...
}
```

- break : 반복문 중단
- continue : 반복문 skip (중단 후 다음 interation 수행)

